## <a name="resource-order_pull">order_pull</a>

Stability: `prototype`

order_pull method RetailOPS webhook API

### order_pull order_pull

Order fetch request.

```
POST /orders
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **action** | *string* | RetailOPS api action name | `"testco.orderpull.order_fetch"` |
| **data:channel:id** | *integer* |  | `21` |
| **data:channel:params:StoreID** | *string* | Store ID | `"yhst-18909142938879050075142"` |
| **data:channel:params:base_uri** | *string* | uri | `"http://172.16.4.130/magento1921"` |
| **data:channel:params:email_invoice** | *integer* | boolean | `0` |
| **data:channel:params:email_return** | *integer* | boolean | `0` |
| **data:channel:params:email_tracking** | *integer* | boolean | `0` |
| **data:channel:params:express_configurable_super_links** | *integer* | boolean | `0` |
| **data:channel:params:import_order_attrs** | *string* |  | `""` |
| **data:channel:params:inv_suspended_instock** | *integer* | boolean | `0` |
| **data:channel:params:inv_suspended_mode** | *integer* |  | `null` |
| **data:channel:params:next_order_refnum** | *integer* | next order reference number | `496` |
| **data:channel:params:order_ack_status_id** | *string* | order acknowledgement status id | `"32"` |
| **data:channel:params:order_fulfilled_status_id** | *string* | order fulfilled status id | `"34"` |
| **data:channel:params:order_in_filfillment_status_id** | *string* | order in fulfillment status id | `"33"` |
| **data:channel:params:push_cancel** | *integer* | boolean | `0` |
| **data:channel:params:unset_other_attributes** | *integer* | boolean | `0` |
| **data:channel:params:unset_other_media** | *integer* | boolean | `0` |
| **data:client_id** | *integer* | RetailOPS client id | `"497"` |
| **data:max_page_size** | *integer* | maximum number of records to include in paged response | `50` |
| **data:order:channel_refnum** | *string* | channel reference number for order | `"496"` |
| **data:page_state** | *integer* |  | `null` |
| **data:single** | *integer* | requesting single order? | `0` |
| **version** | *integer* | RetailOPS api action version | `1` |



#### Curl Example

```bash
$ curl -n -X POST https://yoursite.com/orders \
  -d '{
  "version": 1,
  "action": "testco.orderpull.order_fetch",
  "data": {
    "single": 0,
    "order": {
      "channel_refnum": "496"
    },
    "client_id": "497",
    "channel": {
      "id": 21,
      "params": {
        "StoreID": "yhst-18909142938879050075142",
        "next_order_refnum": 496,
        "order_ack_status_id": "32",
        "order_fulfilled_status_id": "34",
        "order_in_filfillment_status_id": "33",
        "email_return": 0,
        "inv_suspended_instock": 0,
        "unset_other_media": 0,
        "import_order_attrs": "",
        "base_uri": "http://172.16.4.130/magento1921",
        "express_configurable_super_links": 0,
        "unset_other_attributes": 0,
        "push_cancel": 0,
        "inv_suspended_mode": null,
        "email_invoice": 0,
        "email_tracking": 0
      }
    },
    "page_state": null,
    "max_page_size": 50
  }
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "next_page_state": 0,
  "next_order_refnum": 496,
  "orders": [
    {
      "shipping_amt": 0.25,
      "calc_mode": "order",
      "channel_date_created": 1460142547,
      "payment": [
        {
          "params": {
            "channel_refnum": "496",
            "payment_type": "Visa"
          },
          "amount": "1.32",
          "type": "charge"
        }
      ],
      "tax_amt": "0.07",
      "bill_addr": {
        "state_match": "CA",
        "country_match": "US United States",
        "last_name": "Smith",
        "address2": "suite 100",
        "city": "San Diego",
        "postal_code": "92101",
        "address1": "123 Main St",
        "company": "gudTECH",
        "first_name": "John"
      },
      "gift_message": "Happy Birthday",
      "ship_addr": {
        "state_match": "CA",
        "country_match": "US United States",
        "last_name": "Smith",
        "address2": "suite 100",
        "city": "San Diego",
        "postal_code": "92101",
        "address1": "123 Main St",
        "company": "gudTECH",
        "first_name": "John"
      },
      "channel_refnum": "496",
      "customer": {
        "email_address": "john@gudtech.com",
        "phone_number": "5555555555",
        "first_name": "John",
        "last_name": "Smith"
      },
      "discount_amt": 0,
      "shipcode": "Ground (5-7 days)",
      "ip_address": "68.7.2.222",
      "attributes": {
      },
      "items": [
        {
          "channel_refnum": "496",
          "sku": "299",
          "unit_tax": 0,
          "quantity": 1,
          "sku_title": "test",
          "unit_price": "1"
        }
      ]
    }
  ]
}
```

