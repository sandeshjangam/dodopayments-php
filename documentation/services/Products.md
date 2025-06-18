# Products

A list of all methods in the `Products` service. Click on the method name to view detailed information about that method.

| Methods | Description |
| :------ | :---------- |
|[list_products_handler](#list_products_handler)|  |
|[create_product](#create_product)|  |
|[get_product_handler](#get_product_handler)|  |
|[patch_product](#patch_product)|  |
|[delete_product](#delete_product)|  |
|[upload_product_file](#upload_product_file)|  |
|[update_product_image](#update_product_image)|  |
|[undelete_product](#undelete_product)|  |

## list_products_handler


- HTTP Method: `GET`
- Endpoint: `/products`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $pageSize | int | ❌ | Page size default is 10 max is 100 |
| $pageNumber | int | ❌ | Page number default is 0 |
| $archived | bool | ❌ | List archived products |
| $recurring | bool | ❌ | Filter products by pricing type: - `true`: Show only recurring pricing products (e.g. subscriptions) - `false`: Show only one-time price products - `null` or absent: Show both types of products |
| $brandId | string | ❌ | filter by Brand id |

**Return Type**

`Models\GetProductsListResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->products->listProductsHandler(
  pageSize: 9,
  pageNumber: 7,
  archived: true,
  recurring: true,
  brandId: "brand_id"
);

print_r($response);
```

## create_product


- HTTP Method: `POST`
- Endpoint: `/products`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\CreateProductRequest | ✅ |  |

**Return Type**

`Models\GetProductResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\CreateDigitalProductDeliveryRequest;
use Dodopayments\Models\LicenseKeyDuration;
use Dodopayments\Models\Price;
use Dodopayments\Models\TaxCategory;
use Dodopayments\Models\CreateProductRequest;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

COMPLEX_MODEL_NOT_IMPLEMENTED

$taxCategory = Models\TaxCategory::DigitalProducts;

$input = new Models\CreateProductRequest(
  addons: [],
  brandId: "brand_id",
  description: "description",
  digitalProductDelivery: $createDigitalProductDeliveryRequest,
  licenseKeyActivationMessage: "license_key_activation_message",
  licenseKeyActivationsLimit: 9,
  licenseKeyDuration: $licenseKeyDuration,
  licenseKeyEnabled: true,
  name: "name",
  price: $price,
  taxCategory: $taxCategory
);

$response = $sdk->products->createProduct(
  input: $input
);

print_r($response);
```

## get_product_handler


- HTTP Method: `GET`
- Endpoint: `/products/{id}`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $id | string | ✅ | Product Id |

**Return Type**

`Models\GetProductResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->products->getProductHandler(
  id: "id"
);

print_r($response);
```

## patch_product


- HTTP Method: `PATCH`
- Endpoint: `/products/{id}`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\PatchProductRequest | ✅ |  |
| $id | string | ✅ |  |

**Return Type**

`mixed`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\PatchDigitalProductDeliveryRequest;
use Dodopayments\Models\LicenseKeyDuration;
use Dodopayments\Models\Price;
use Dodopayments\Models\TaxCategory;
use Dodopayments\Models\PatchProductRequest;

$sdk = new Client(accessToken: 'YOUR_TOKEN');


$input = new Models\PatchProductRequest(
  addons: [],
  brandId: "brand_id",
  description: "description",
  digitalProductDelivery: $patchDigitalProductDeliveryRequest,
  imageId: "image_id",
  licenseKeyActivationMessage: "license_key_activation_message",
  licenseKeyActivationsLimit: 9,
  licenseKeyDuration: $licenseKeyDuration,
  licenseKeyEnabled: true,
  name: "name",
  price: $price,
  taxCategory: $taxCategory
);

$response = $sdk->products->patchProduct(
  input: $input,
  id: "id"
);

print_r($response);
```

## delete_product


- HTTP Method: `DELETE`
- Endpoint: `/products/{id}`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $id | string | ✅ |  |

**Return Type**

`mixed`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->products->deleteProduct(
  id: "id"
);

print_r($response);
```

## upload_product_file


- HTTP Method: `PUT`
- Endpoint: `/products/{id}/files`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\UploadProductFile | ✅ |  |
| $id | string | ✅ | Product Id |

**Return Type**

`Models\UploadProductFileResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\UploadProductFile;

$sdk = new Client(accessToken: 'YOUR_TOKEN');


$input = new Models\UploadProductFile(
  fileName: "file_name"
);

$response = $sdk->products->uploadProductFile(
  input: $input,
  id: "id"
);

print_r($response);
```

## update_product_image


- HTTP Method: `PUT`
- Endpoint: `/products/{id}/images`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $id | string | ✅ | Product Id |
| $forceUpdate | bool | ❌ |  |

**Return Type**

`Models\UpdateProductImageResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->products->updateProductImage(
  forceUpdate: true,
  id: "id"
);

print_r($response);
```

## undelete_product


- HTTP Method: `POST`
- Endpoint: `/products/{id}/unarchive`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $id | string | ✅ |  |

**Return Type**

`mixed`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->products->undeleteProduct(
  id: "id"
);

print_r($response);
```




<!-- This file was generated by liblab | https://liblab.com/ -->