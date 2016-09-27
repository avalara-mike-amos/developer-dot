---
layout: page
title: PasswordMinComplexityError
number: 12
categories: [AvaTax Error Codes]
disqus: 0
---

## Summary

This password does not meet the complexity requirements set by AvaTax.

## Example

    {
      "code": "PasswordMinComplexityError",
      "target": "Unknown",
      "details": [
        {
          "code": "PasswordMinComplexityError",
          "number": 0,
          "message": "Passwords must be a combination of upper/lower case, numbers, and non-alphanumeric characters.",
          "faultCode": "Client",
          "helpLink": "http://developer.avalara.com/avatax/errors/PasswordMinComplexityError",
          "severity": "Error"
        }
      ]
    }

## Explanation

Passwords for AvaTax must obey certain complexity requirements. 

This password is not permitted because it lacks certain complexity features.