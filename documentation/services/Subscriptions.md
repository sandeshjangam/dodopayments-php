# Subscriptions

A list of all methods in the `Subscriptions` service. Click on the method name to view detailed information about that method.

| Methods | Description |
| :------ | :---------- |
|[list_subscriptions_handler](#list_subscriptions_handler)|  |
|[create_subscription_handler](#create_subscription_handler)|  |
|[get_subscription_handler](#get_subscription_handler)|  |
|[patch_subscription_handler](#patch_subscription_handler)|  |
|[update_subscription_plan_handler](#update_subscription_plan_handler)|  |
|[create_subscription_charge](#create_subscription_charge)|  |

## list_subscriptions_handler


- HTTP Method: `GET`
- Endpoint: `/subscriptions`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $createdAtGte | string | ❌ | Get events after this created time |
| $createdAtLte | string | ❌ | Get events created before this time |
| $pageSize | int | ❌ | Page size default is 10 max is 100 |
| $pageNumber | int | ❌ | Page number default is 0 |
| $customerId | string | ❌ | Filter by customer id |
| $status | Models\SubscriptionStatus | ❌ | Filter by status |

**Return Type**

`Models\GetSubscriptionsListResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$status = Models\SubscriptionStatus::Pending;

$response = $sdk->subscriptions->listSubscriptionsHandler(
  createdAtGte: "created_at_gte",
  createdAtLte: "created_at_lte",
  pageSize: 5,
  pageNumber: 123,
  customerId: "customer_id",
  status: $status
);

print_r($response);
```

## create_subscription_handler


- HTTP Method: `POST`
- Endpoint: `/subscriptions`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\CreateSubscriptionRequest | ✅ |  |

**Return Type**

`Models\CreateSubscriptionResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\AttachAddonReq;
use Dodopayments\Models\PaymentMethodTypes;
use Dodopayments\Models\BillingAddress;
use Dodopayments\Models\Currency;
use Dodopayments\Models\CustomerRequest;
use Dodopayments\Models\OnDemandSubscriptionReq;
use Dodopayments\Models\CreateSubscriptionRequest;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$countryCodeAlpha2 = Models\CountryCodeAlpha2::Af;

$billingAddress = new Models\BillingAddress(
  city: "city",
  country: $countryCodeAlpha2,
  state: "state",
  street: "street",
  zipcode: "zipcode"
);

COMPLEX_MODEL_NOT_IMPLEMENTED

$input = new Models\CreateSubscriptionRequest(
  addons: [],
  allowedPaymentMethodTypes: [],
  billing: $billingAddress,
  billingCurrency: $currency,
  customer: $customerRequest,
  discountCode: "discount_code",
  metadata: [],
  onDemand: $onDemandSubscriptionReq,
  paymentLink: true,
  productId: "product_id",
  quantity: 9,
  returnUrl: "return_url",
  showSavedPaymentMethods: true,
  taxId: "tax_id",
  trialPeriodDays: 6
);

$response = $sdk->subscriptions->createSubscriptionHandler(
  input: $input
);

print_r($response);
```

## get_subscription_handler


- HTTP Method: `GET`
- Endpoint: `/subscriptions/{subscription_id}`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| $subscriptionId | string | ✅ | Subscription Id |

**Return Type**

`Models\SubscriptionResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$response = $sdk->subscriptions->getSubscriptionHandler(
  subscriptionId: "subscription_id"
);

print_r($response);
```

## patch_subscription_handler


- HTTP Method: `PATCH`
- Endpoint: `/subscriptions/{subscription_id}`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\PatchSubscriptionRequest | ✅ |  |
| $subscriptionId | string | ✅ | Subscription Id |

**Return Type**

`Models\SubscriptionResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\BillingAddress;
use Dodopayments\Models\DisableOnDemandReq;
use Dodopayments\Models\SubscriptionStatus;
use Dodopayments\Models\PatchSubscriptionRequest;

$sdk = new Client(accessToken: 'YOUR_TOKEN');


$input = new Models\PatchSubscriptionRequest(
  billing: $billingAddress,
  disableOnDemand: $disableOnDemandReq,
  metadata: [],
  status: $subscriptionStatus,
  taxId: "tax_id"
);

$response = $sdk->subscriptions->patchSubscriptionHandler(
  input: $input,
  subscriptionId: "subscription_id"
);

print_r($response);
```

## update_subscription_plan_handler


- HTTP Method: `POST`
- Endpoint: `/subscriptions/{subscription_id}/change-plan`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\UpdateSubscriptionPlanReq | ✅ |  |
| $subscriptionId | string | ✅ | Subscription Id |

**Return Type**

`mixed`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\AttachAddonReq;
use Dodopayments\Models\ProrationBillingMode;
use Dodopayments\Models\UpdateSubscriptionPlanReq;

$sdk = new Client(accessToken: 'YOUR_TOKEN');

$prorationBillingMode = Models\ProrationBillingMode::ProratedImmediately;

$input = new Models\UpdateSubscriptionPlanReq(
  addons: [],
  productId: "product_id",
  prorationBillingMode: $prorationBillingMode,
  quantity: 4
);

$response = $sdk->subscriptions->updateSubscriptionPlanHandler(
  input: $input,
  subscriptionId: "subscription_id"
);

print_r($response);
```

## create_subscription_charge


- HTTP Method: `POST`
- Endpoint: `/subscriptions/{subscription_id}/charge`

**Parameters**

| Name    | Type| Required | Description |
| :-------- | :----------| :----------| :----------|
| input | Models\CreateSubscriptionChargeRequest | ✅ |  |
| $subscriptionId | string | ✅ | Subscription Id |

**Return Type**

`Models\CreateSubscriptionChargeResponse`

**Example Usage Code Snippet**
```php
<?php

use Dodopayments\Client;
use Dodopayments\Models\CreateSubscriptionChargeRequest;

$sdk = new Client(accessToken: 'YOUR_TOKEN');


$input = new Models\CreateSubscriptionChargeRequest(
  productPrice: 8
);

$response = $sdk->subscriptions->createSubscriptionCharge(
  input: $input,
  subscriptionId: "subscription_id"
);

print_r($response);
```




<!-- This file was generated by liblab | https://liblab.com/ -->