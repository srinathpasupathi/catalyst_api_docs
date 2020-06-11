# Errors

Catalyst API uses the following error codes:

Error Code | Description | HTTP Status Code
--------- | ------- | ----------- | 
API_LIMIT_REACHED | The API limit for your account is exceeded. Upgrade your license plan. | 403
CONFLICT | Contradicts with the existing value. Try giving another value. | 409
DUPLICATE_ENTRY | The email ID you have entered already exists. Please provide a different email ID. | 409
DUPLICATE_ENTRY | The domain name already exists. Please provide a different value. | 409
DUPLICATE_OPERATION | The requested operation is already under progress. Please wait until it is completed. | 409
DUPLICATE_VALUE | The value you have entered already exists. Please provide a different value. | 409
EMAIL_ERROR | Email sending process failed. Try after some time. | 500
EXPIRED | The requested resource has expired. Please try creating it again. | 410
EXPIRED_LOG | The response log you are trying to download is expired. | 410
FUNCTION_ERROR | Encountered an internal server error. | 202
INTERNAL_SERVER_ERROR | Encountered an internal server error. | 500
INVALID_CONTENT | The given input is not in an acceptable format. | 403
INVALID_ID | The resource ID you have provided does not exist. | 404
INVALID_INPUT | The table name you have provided does not exist. | 400
INVALID_INPUT | The column name you have provided does not exist. | 400
INVALID_INPUT | The foreign key you have provided doesn't match with the ROWID of the parent table. | 400
INVALID_INPUT | The input you have provided is not valid. | 400
INVALID_NAME | The email ID you have provided does not exist. | 404
INVALID_NAME | The table name you have provided does not exist. | 404
INVALID_OPERATION | The requested operation is invalid. | 403
INVALID_REQUEST_METHOD | The requested method is not accepted. | 405
MISMATCH | The value provided does not match with the expected one. | 400
MISSING_FUNCTION | The function ID you have provided does not exists. | 400
MISSING_VALUE | The expected input is missing. | 400
NO_ACCESS | You don't have privileges to perform this action | 401
NO_CONTENT_AVAILABLE | The request returned an empty response. | 204
UNAUTHORISED | You are not authorised to perform this action. | 401
VERIFICATION_NEEDED | Your email address needs to be verified. | 403
ZCQL_QUERY_ERROR | The format of your query is invalid. | 400
