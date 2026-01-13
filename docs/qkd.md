# Documentation for ETSI GS QKD 004 push mode specification, QKD server

<a name="documentation-for-api-endpoints"></a>
## Documentation for API Endpoints

All URIs are relative to *https://qkd_server/api/v1/kms/etsi004*

| Class | Method | HTTP request | Description |
|------------ | ------------- | ------------- | -------------|
| *Etsi004Api* | [**getKey**](Apis/Etsi004Api.md#getKey) | **GET** /get-key | start pushed key retrieval process |
*Etsi004Api* | [**postOpenConnect**](Apis/Etsi004Api.md#postOpenConnect) | **POST** /open-connect | open key stream |
*Etsi004Api* | [**putClose**](Apis/Etsi004Api.md#putClose) | **PUT** /close | close the key stream |


<a name="documentation-for-models"></a>
## Documentation for Models

 - [get_key_205_response](./Models/get_key_205_response.md)
 - [get_key_request](./Models/get_key_request.md)
 - [metadata](./Models/metadata.md)
 - [post_open_connect_201_response](./Models/post_open_connect_201_response.md)
 - [post_open_connect_request](./Models/post_open_connect_request.md)
 - [put_close_204_response](./Models/put_close_204_response.md)
 - [put_close_request](./Models/put_close_request.md)
 - [qos](./Models/qos.md)


<a name="documentation-for-authorization"></a>
## Documentation for Authorization

All endpoints do not require authorization.
# Etsi004Api

All URIs are relative to *https://qkd_server/api/v1/kms/etsi004*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getKey**](Etsi004Api.md#getKey) | **GET** /get-key | start pushed key retrieval process |
| [**postOpenConnect**](Etsi004Api.md#postOpenConnect) | **POST** /open-connect | open key stream |
| [**putClose**](Etsi004Api.md#putClose) | **PUT** /close | close the key stream |


<a name="getKey"></a>
# **getKey**
> get_key_205_response getKey(get\_key\_request)

start pushed key retrieval process

    The &#x60;get-key&#x60; message is the starting point after which the QKD device can start pushing keys.

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **get\_key\_request** | [**get_key_request**](../Models/get_key_request.md)|  | |

### Return type

[**get_key_205_response**](../Models/get_key_205_response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

<a name="postOpenConnect"></a>
# **postOpenConnect**
> post_open_connect_201_response postOpenConnect(post\_open\_connect\_request)

open key stream

    The &#x60;open-connect&#x60; message connects a KMS to the QKD Device. Conforming to the specification, the QKD device will assign the &#x60;key_stream_id&#x60; and can suggest alternative QoS due to its capabilities.

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **post\_open\_connect\_request** | [**post_open_connect_request**](../Models/post_open_connect_request.md)|  | |

### Return type

[**post_open_connect_201_response**](../Models/post_open_connect_201_response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

<a name="putClose"></a>
# **putClose**
> put_close_204_response putClose(put\_close\_request)

close the key stream

    The &#x60;close&#x60; message disconnects the KMS from the QKD device.

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **put\_close\_request** | [**put_close_request**](../Models/put_close_request.md)|  | |

### Return type

[**put_close_204_response**](../Models/put_close_204_response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

# get_key_205_response
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **status** | **Integer** |  | [default to null] |
| **metadata** | [**metadata**](metadata.md) |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# get_key_request
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key\_stream\_id** | **UUID** | corresponding to the one given in &#x60;open_connect&#x60; | [default to null] |
| **index** | **Integer** | increasing index of the key chunk in the key stream. Wrapping at UINT_MAX. | [optional] [default to null] |
| **metadata** | [**metadata**](metadata.md) |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# metadata
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **size** | **Integer** | size of buffer in characters | [optional] [default to null] |
| **buffer** | **String** | metadata in json format. | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_open_connect_201_response
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **source** | **URI** | the source URI of the request. | [default to null] |
| **destination** | **URI** | the destination URI of the request. | [default to null] |
| **key\_stream\_id** | **UUID** | key stream ID. If not specified it is up to the QKD device to define the UUID | [optional] [default to null] |
| **qos** | [**qos**](qos.md) | requested QoS | [default to null] |
| **status** | **Integer** |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_open_connect_request
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **source** | **URI** | the source URI of the request. | [default to null] |
| **destination** | **URI** | the destination URI of the request. | [default to null] |
| **key\_stream\_id** | **UUID** | key stream ID. If not specified it is up to the QKD device to define the UUID | [optional] [default to null] |
| **qos** | [**qos**](qos.md) | requested QoS | [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# put_close_204_response
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **status** | **Integer** |  | [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# put_close_request
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key\_stream\_id** | **UUID** | corresponding to the one given in &#x60;open_connect&#x60; | [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# qos
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key\_chunk\_size** | **Integer** | length of key chunks in Byte. | [optional] [default to null] |
| **max\_bps** | **Integer** | in bit per second | [optional] [default to null] |
| **min\_bps** | **Integer** | in bit per second | [optional] [default to null] |
| **jitter** | **Integer** | in bit per second | [optional] [default to null] |
| **priority** | **Integer** | Meaning up to implementation. | [optional] [default to null] |
| **timeout** | **Integer** | Timeout in msec after which the call will be aborted, returning an error. | [optional] [default to null] |
| **ttl** | **Integer** | Time in seconds after which the keys for this key stream ID shall be erased from the kms key store. | [optional] [default to null] |
| **metadata\_mimetype** | **String** | MIME type of the metadata of the &#x60;get&#x60; request | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

