import json
import urllib3
http =urllib3.PoolManager()

def sendEmail(name,mobile_number,email):
    data={"emailId":email,"name":name,"mobile_number": mobile_number}
    encoded_data = json.dumps(data).encode('utf-8')
    response = http.request('POST',"http://367eb369.ngrok.io/sendmail",headers={'Content-Type':'application/json'},body =encoded_data )
    return response.data.decode('utf-8')
def lambda_handler(event, context):
    # TODO implement
    name=event['currentIntent']['slots']['name']
    mobile_number=event['currentIntent']['slots']['mobile_number']
    email=event['currentIntent']['slots']['emailId']
    result =sendEmail(name,mobile_number,email)
    response = {
        "dialogAction":{
            "type":"Close",
            "fulfillmentState":"Fulfilled",
            "message": {
                "contentType": "SSML" ,
                "content": "{} Please let us know if we can assist you with any other information.".format(result)
            },
        }
    }
    return response
