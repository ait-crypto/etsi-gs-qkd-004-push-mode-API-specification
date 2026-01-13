# Documentation for ETSI GS QKD 004 push mode specification, KMS server

<a name="documentation-for-api-endpoints"></a>
## Documentation for API Endpoints

All URIs are relative to *https://qkd_server/api/v1/qkd/etsi004*

| Class | Method | HTTP request | Description |
|------------ | ------------- | ------------- | -------------|
| *Etsi004Api* | [**postKeyMaterial**](Apis/Etsi004Api.md#postKeyMaterial) | **POST** /key-material | endpoint to push key material to. |


<a name="documentation-for-models"></a>
## Documentation for Models

 - [post_key_material_201_response](./Models/post_key_material_201_response.md)
 - [post_key_material_201_response_metadata](./Models/post_key_material_201_response_metadata.md)
 - [post_key_material_request](./Models/post_key_material_request.md)
 - [post_key_material_request_metadata](./Models/post_key_material_request_metadata.md)
 - [post_key_material_request_metadata_buffer](./Models/post_key_material_request_metadata_buffer.md)


<a name="documentation-for-authorization"></a>
## Documentation for Authorization

All endpoints do not require authorization.
# Etsi004Api

All URIs are relative to *https://qkd_server/api/v1/qkd/etsi004*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**postKeyMaterial**](Etsi004Api.md#postKeyMaterial) | **POST** /key-material | endpoint to push key material to. |


<a name="postKeyMaterial"></a>
# **postKeyMaterial**
> post_key_material_201_response postKeyMaterial(post\_key\_material\_request)

endpoint to push key material to.

    According to the sequence, after a successful &#x60;get_key&#x60;, the QKD can push the corresponding key material to this endpoint, whenever it created a new key.

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **post\_key\_material\_request** | [**post_key_material_request**](../Models/post_key_material_request.md)|  | |

### Return type

[**post_key_material_201_response**](../Models/post_key_material_201_response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

# post_key_material_201_response
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **status** | **Integer** |  | [default to null] |
| **metadata** | [**post_key_material_201_response_metadata**](post_key_material_201_response_metadata.md) |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_key_material_201_response_metadata
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **size** | **Integer** | size of buffer in characters | [optional] [default to null] |
| **buffer** | **String** | metadata in json format. | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_key_material_request
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **status** | **Integer** |  | [default to null] |
| **index** | **Integer** | increasing index of the key chunk in the key stream. Wrapping at UINT_MAX. | [default to null] |
| **key\_buffer** | **String** |  | [default to null] |
| **metadata** | [**post_key_material_request_metadata**](post_key_material_request_metadata.md) |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_key_material_request_metadata
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **size** | **Integer** | size of buffer in characters | [optional] [default to null] |
| **buffer** | [**post_key_material_request_metadata_buffer**](post_key_material_request_metadata_buffer.md) |  | [optional] [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

# post_key_material_request_metadata_buffer
## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **key\_stream\_id** | **UUID** | key stream ID to which the value belongs (required for KMS in case of multiple open key streams) | [default to null] |

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

