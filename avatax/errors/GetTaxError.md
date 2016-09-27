---
layout: page
title: GetTaxError
number: 300
categories: [AvaTax Error Codes]
disqus: 0
---

## Summary

A problem occurred when you attempted to create a transaction through AvaTax.

## Example

    {
      "code": "GetTaxError",
      "target": "Unknown",
      "details": [
        {
          "code": "GetTaxError",
          "number": 300,
          "message": "",
          "description": "-0-, -1-, -2-, -3-, -4-, -5-, -6-, -7-, -8-, -9-",
          "helpLink": "http://developer.avalara.com/avatax/errors/GetTaxError",
          "severity": "Error"
        }
      ]
    }

## Explanation

Creating a transaction was known as "GetTax" in Avalara's SOAP API.  For compatibility reasons, this error message is also labeled a "GetTax" error message.

Please refer to the details section for specific details about this error message and next steps.