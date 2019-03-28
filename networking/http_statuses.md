---
layout: default
title: HTTP Statuses
parent: Networking
nav_order: 1
---

# HTTP Statuses Cheatsheet

---

This list does not include non-standard status codes.

---

## 1xx Informational

| Status  | Meaning                | Rails HTTP Symbol |
|:--------|:-----------------------|:------------------|
| __100__ | Continue               | `:continue`       |
| __101__ | Switching Protocols    | `:switching_protocols` |
| __102__ | Processing             | `:processing`     |

---

## 2xx Success

| Status  | Meaning                | Rails HTTP Symbol |
|:--------|:-----------------------|:------------------|
| __200__ | OK                     | `:ok`             |
| __201__ | Created                | `:created`        |
| __202__ | Accepted               | `:accepted`       |
| __203__ | Non-authoritative Information | `:non_authoritative_information` |
| __204__ | No Content             | `:no_content`     |
| __205__ | Reset Content          | `:reset_content`  |
| __206__ | Partial Content        | `:partial_content` |
| __207__ | Multi-Status           | `:multi_status`       |
| __208__ | Already Reported       | `:already_reported`   |
| __226__ | IM Used                | `:im_used`        |

---

## 3xx Redirection

| Status  | Meaning                | Rails HTTP Symbol     |
|:--------|:-----------------------|:----------------------|
| __300__ | Multiple Choices       | `:multiple_choices`   |
| __301__ | Moved Permanently      | `:moved_permanently`  |
| __302__ | Found                  | `:found`              |
| __303__ | See Other              | `:see_other`          |
| __304__ | Not Modified           | `:not_modified`       |
| __305__ | Use Proxy              | `:use_proxy`          |
| __307__ | Temporary Redirect     | `:temporary_redirect` |
| __308__ | Permanent Redirect     | `:permanent_redirect` |

---

## 4xx Client Error

| Status  | Meaning                | Rails HTTP Symbol     |
|:--------|:-----------------------|:----------------------|
| __400__ | Bad Request            | `:bad_request`        |
| __401__ | Unauthorized           | `:unauthorized`       |
| __402__ | Payment Required       | `:payment_required`   |
| __403__ | Forbidden              | `:forbidden`          |
| __404__ | Not Found              | `:not_found`          |
| __405__ | Method Not Allowed     | `:method_not_allowed` |
| __406__ | Not Acceptable         | `:not_acceptable`     |
| __407__ | Proxy Authentication Required | `:proxy_authentication_required` |
| __408__ | Request Timeout        | `:request_timeout`    |
| __409__ | Conflict               | `:conflict`           |
| __410__ | Gone                   | `:gone`               |
| __411__ | Length Required        | `:length_required`    |
| __412__ | Precondition Failed    | `:precondition_failed`|
| __413__ | Request Entity Too Large | `:request_entity_too_large` |
| __414__ | Request Uri Too Long     | `:request_uri_too_long`     |
| __415__ | Unsupported Media Type   | `:unsupported_media_type`   |
| __416__ | Requested Range Not Satisfiable | `:requested_range_not_satisfiable` |
| __418__ | I'm a teapot             | Not implemented            |
| __421__ | Misdirected Request      | `:misdirected_request`     |
| __422__ | Unprocessable Entity     | `:unprocessable_entity`    |
| __423__ | Locked                   | `:locked`                  |
| __424__ | Failed Dependency        | `:failed_dependency`       |
| __426__ | Upgrade Required         | `:upgrade_required`        |
| __428__ | Precondition Required    | `:precondition_required`   |
| __429__ | Too Many Requests        | `:too_many_requests`       |
| __424__ | Failed Dependency        | `:failed_dependency`       |
| __431__ | Request Header Fields Too Large | `:request_header_fields_too_large` |
| __451__ | Unavailable For Legal Reasons | `:unavailable_for_legal_reasons` |

---

## 5xx Server Error

| Status  | Meaning                | Rails HTTP Symbol     |
|:--------|:-----------------------|:----------------------|
| __500__ | Internal Server Error  | `:internal_server_error` |
| __501__ | Not Implemented        | `:not_implemented`       |
| __502__ | Bad Gateway            | `:bad_gateway`           |
| __503__ | Service Unavailable    | `:service_unavailable`   |
| __504__ | Gateway Timeout        | `:gateway_timeout`       |
| __505__ | Http Version Not Supported | `:http_version_not_supported` |
| __506__ | Variant Also Negotiates | `:variant_also_negotiates` |
| __507__ | Insufficient Storage    | `:insufficient_storage`    |
| __508__ | Loop Detected           | `:loop_detected`           |
| __510__ | Not Extended            | `:not_extended`            |
| __511__ | Network Authentication Required | `:network_authentication_required` |

---

## Notes

To get list of available status codes in Rails/Rack

```rb
# https://github.com/rack/rack/blob/9d25a133fa7651e60e23a46ef0b732fd131d3458/lib/rack/utils.rb#L494
Rack::Utils::HTTP_STATUS_CODES
Rack::Utils::SYMBOL_TO_STATUS_CODE
```
