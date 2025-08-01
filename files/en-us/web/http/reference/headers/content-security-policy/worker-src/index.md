---
title: "Content-Security-Policy: worker-src directive"
short-title: worker-src
slug: Web/HTTP/Reference/Headers/Content-Security-Policy/worker-src
page-type: http-csp-directive
browser-compat: http.headers.Content-Security-Policy.worker-src
sidebar: http
---

The HTTP {{HTTPHeader("Content-Security-Policy")}} (CSP)
**`worker-src`** directive specifies valid sources for
{{domxref("Worker")}}, {{domxref("SharedWorker")}}, or {{domxref("ServiceWorker")}}
scripts.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">CSP version</th>
      <td>3</td>
    </tr>
    <tr>
      <th scope="row">Directive type</th>
      <td>{{Glossary("Fetch directive")}}</td>
    </tr>
    <tr>
      <th scope="row">Fallback</th>
      <td>
        <p>
          If this directive is absent, the user agent will first look for the
          {{CSP("child-src")}} directive, then the
          {{CSP("script-src")}} directive, then finally for the
          {{CSP("default-src")}} directive, when governing worker
          execution.
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Syntax

```http
Content-Security-Policy: worker-src 'none';
Content-Security-Policy: worker-src <source-expression-list>;
```

This directive may have one of the following values:

- `'none'`
  - : No resources of this type may be loaded. The single quotes are mandatory.
- `<source-expression-list>`
  - : A space-separated list of _source expression_ values. Resources of this type may be loaded if they match any of the given source expressions. For this directive, the following source expression values are applicable:
    - [`<host-source>`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#host-source)
    - [`<scheme-source>`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#scheme-source)
    - [`'self'`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#self)

## Examples

### Violation cases

Given this CSP header:

```http
Content-Security-Policy: worker-src https://example.com/
```

{{domxref("Worker")}}, {{domxref("SharedWorker")}}, {{domxref("ServiceWorker")}} are
blocked and won't load:

```html
<script>
  let blockedWorker = new Worker("data:text/javascript,…");
  blockedWorker = new SharedWorker("https://not-example.com/");
  navigator.serviceWorker.register("https://not-example.com/sw.js");
</script>
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTTPHeader("Content-Security-Policy")}}
- [CSP for Web Workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers#content_security_policy)
- {{domxref("Worker")}}, {{domxref("SharedWorker")}}, {{domxref("ServiceWorker")}}
