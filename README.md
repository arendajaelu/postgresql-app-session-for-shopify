# postgresql-app-session-for-shopify
Shopify App Session Storage for PostgreSQL with bugfixing

This package fixed two potential issues:

1. Add “CREATE TABLE IF NOT EXISTS” into the createTable function
2. Amend the field "scope" from varchar to text (supports over 255 chars in app scope)


# Session Storage Adapter for PostgreSQL

This package implements the `SessionStorage` interface that works with an instance of [PostgreSQL](https://www.postgresql.org).

```js
import {shopifyApp} from '@shopify/shopify-app-express';
import {PostgreSQLSessionStorage} from '@shopify/shopify-app-session-storage-postgresql';

const shopify = shopifyApp({
  sessionStorage: new PostgreSQLSessionStorage(
    'postgres://username:password@host/database',
  ),
  // ...
});

// OR

const shopify = shopifyApp({
  sessionStorage: PostgreSQLSessionStorage.withCredentials(
    'host.com',
    'thedatabase',
    'username',
    'password',
  ),
  // ...
});
```

If you prefer to use your own implementation of a session storage mechanism that is compatible with the `@shopify/shopify-app-express` package, see the [implementing session storage guide](../shopify-app-session-storage/implementing-session-storage.md).
