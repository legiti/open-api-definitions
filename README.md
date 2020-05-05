# open-api-defs
Repository for Legiti OpenAPI definitions. Our official API definitions can be found as follows:
- [Ticketing](https://github.com/legiti/open-api-defs/blob/master/ticketing/v1_resolved.yml)
- [Delivery](https://github.com/legiti/open-api-defs/blob/master/delivery/v1_resolved.yml)


## Using the SDKS
Legiti does not currently publish or maintain an official version of our collection SDKs. The SDKs that can be autogenerated from our OpenAPI definition should be treated as such: autogenerated. Please refer to our [official documentation](https://docs.legiti.com) for documentation that has been written and edited with love and care by human beings.

That said, the SDKs that can be generated from our OpenAPI definition should be completely functional and ready for use within your company's applications. Refer to SwaggerHub for a [list of supported languages](https://app.swaggerhub.com/help/apis/generating-code/index) for client SDK generation (OpenAPI v3.0.1)

### Python
You can generate the Python SDK from SwaggerHub [here](https://app.swaggerhub.com/apis/LegitiTech/legiti-ticketing_api/1.0) (click Export > Client SDK > Python). This will autogenerate and download a zipped Python client for our API. You can use it as follows:

```
unzip $zipped_python_sdk $directory_to_unzip_it
cd $directory_to_unzip_it
python setup.py install
```

The SDK is now available within your Python environment as follows:
```
>>> import swagger_client as legiti_sdk
>>>
>>>
>>> legiti_client = legiti_sdk.ApiClient(header_name='Authorization', 
...                                          header_value='Bearer $API_KEY')
>>> auth_api = legiti_sdk.AuthApi(legiti_client)
>>> body = legiti_sdk.BodyAuth(user_id='1234', action_type='logout')
>>> response = auth_api.auth_post(body=body)
>>> print(response)
{'message': 'Valid create request!'}
```

## Developing
- OpenAPI Editor plugin for VSCode highly recommended
- [speccy](https://github.com/wework/speccy) required for file resolution (`npm install -g speccy`)

### Generating the OpenAPI definition

Our definitions are separated into a few distinct pages, so if you want to iterate on them and generate a new complete page, you'll need to use speccy to resolve the separated files. For example, if you wanted to resolve our Ticketing API definition: 

```
cd ticketing/
speccy resolve v1.yml > v1_resolved.yml
```

`v1_resolved.yml` will contain the complete API definition, which you can then paste into SwaggerHub to generate SDKs, server stubs, or import to Postman. 
