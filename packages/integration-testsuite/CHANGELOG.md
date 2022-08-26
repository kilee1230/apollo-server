# @apollo/server-integration-testsuite

## 4.0.0-alpha.8

### Patch Changes

- Updated dependencies [[`3320fee92`](https://github.com/apollographql/apollo-server/commit/3320fee922ffa50080aa63597c84844516583860), [`9fc23f799`](https://github.com/apollographql/apollo-server/commit/9fc23f7995205e8239890197dbeaabc5db6fb073), [`2cab8f785`](https://github.com/apollographql/apollo-server/commit/2cab8f78580f6dacc64a497d06397b5b3cce89f6)]:
  - @apollo/server@4.0.0-alpha.8

## 4.0.0-alpha.7

### Patch Changes

- [#6817](https://github.com/apollographql/apollo-server/pull/6817) [`eca003fdc`](https://github.com/apollographql/apollo-server/commit/eca003fdc75bdb63153e68119b9891d2bffc6545) Thanks [@glasser](https://github.com/glasser)! - Move ApolloServerPluginGraphQLPlayground into its own package.

- Updated dependencies [[`eca003fdc`](https://github.com/apollographql/apollo-server/commit/eca003fdc75bdb63153e68119b9891d2bffc6545)]:
  - @apollo/server-plugin-landing-page-graphql-playground@4.0.0-alpha.0
  - @apollo/server@4.0.0-alpha.7

## 4.0.0-alpha.6

### Patch Changes

- [#6814](https://github.com/apollographql/apollo-server/pull/6814) [`cf0fcf49a`](https://github.com/apollographql/apollo-server/commit/cf0fcf49afa9b8ee12840f5ac4bf1be6320cb7e1) Thanks [@glasser](https://github.com/glasser)! - Several changes relating to plugins:

  - Remove the `server` field on `GraphQLRequestContext` and `GraphQLServerContext` (ie, the arguments to most plugin hook methods). This was added during AS4 development and did not exist in AS3.

  - Add `logger` and `cache` fields to `GraphQLRequestContext` and `GraphQLServerContext`. The `logger` fields and `GraphQLRequestContext.cache` existed in AS3 and had been previously removed for redundancy with the `server` field. (Unlike in AS3, `logger` is readonly.)

  - `ApolloServerPlugin` is now declared as `<in TContext extends BaseContext = BaseContext>` rather than `<in out TContext>`. This means that you can declare a plugin that doesn't care about `contextValue` to simply implement `ApolloServerPlugin` and it will work with any `ApolloServer<NoMatterWhatContext>`. This should make it easy to write plugins that don't care about context.

  - Remove the ability to specify a factory function as an element of the `plugins` list in the `ApolloServer` constructor. (Reducing the number of ways to specify constructor options helps keep type errors simpler.) As far as we know the main use case for this (referring to the `ApolloServer` itself when creating the plugin) can be handled with the new-in-AS4 `ApolloServer.addPlugin` method.

- Updated dependencies [[`cf0fcf49a`](https://github.com/apollographql/apollo-server/commit/cf0fcf49afa9b8ee12840f5ac4bf1be6320cb7e1)]:
  - @apollo/server@4.0.0-alpha.6

## 4.0.0-alpha.5

### Patch Changes

- [#6806](https://github.com/apollographql/apollo-server/pull/6806) [`bccc230f0`](https://github.com/apollographql/apollo-server/commit/bccc230f05761c15098df9a5e9f57f0c65cf4fa6) Thanks [@glasser](https://github.com/glasser)! - Rename response.http.statusCode back to status like it was in AS3.

- Updated dependencies [[`bccc230f0`](https://github.com/apollographql/apollo-server/commit/bccc230f05761c15098df9a5e9f57f0c65cf4fa6)]:
  - @apollo/server@4.0.0-alpha.5

## 4.0.0-alpha.4

### Patch Changes

- [#6795](https://github.com/apollographql/apollo-server/pull/6795) [`363fd308d`](https://github.com/apollographql/apollo-server/commit/363fd308d09c8df0428b059cbe6743a723ac65b2) Thanks [@bonnici](https://github.com/bonnici)! - Added unit tests to cover `unmodified` and `masked` error reporting options

* [#6794](https://github.com/apollographql/apollo-server/pull/6794) [`7445d3377`](https://github.com/apollographql/apollo-server/commit/7445d3377d16cdc65506131572c0a616d3a6324c) Thanks [@glasser](https://github.com/glasser)! - Usage reporting and inline trace plugins: replace `rewriteError` with `sendErrorsInTraces`/`includeErrors`, and mask all errors by default.

* Updated dependencies [[`13f809ca6`](https://github.com/apollographql/apollo-server/commit/13f809ca6c5e1f0be9d05823f1194a8743321a79), [`96178c570`](https://github.com/apollographql/apollo-server/commit/96178c57070af574fbcff7f51b73924c576725db), [`400f7867b`](https://github.com/apollographql/apollo-server/commit/400f7867b521359fd7213547c88fcf3fc8fbe94c), [`7445d3377`](https://github.com/apollographql/apollo-server/commit/7445d3377d16cdc65506131572c0a616d3a6324c)]:
  - @apollo/server@4.0.0-alpha.4

## 4.0.0-alpha.3

### Patch Changes

- [#6771](https://github.com/apollographql/apollo-server/pull/6771) [`bce9150f3`](https://github.com/apollographql/apollo-server/commit/bce9150f31d6fd58b7a6622611ec7b35b3564aa6) Thanks [@glasser](https://github.com/glasser)! - Support Gateway. Remove executor constructor option.

* [#6764](https://github.com/apollographql/apollo-server/pull/6764) [`c4115e96a`](https://github.com/apollographql/apollo-server/commit/c4115e96ac75e04cffe1c3353fc03ea65dcab909) Thanks [@glasser](https://github.com/glasser)! - Get cache-control types from @apollo/cache-control-types; no more `declare module` for info.cacheControl

- [#6759](https://github.com/apollographql/apollo-server/pull/6759) [`6ef6a090c`](https://github.com/apollographql/apollo-server/commit/6ef6a090cff26f5d98e9965cd839307931e12516) Thanks [@glasser](https://github.com/glasser)! - Refactor error formatting.

  Remove `error.extensions.exception`; you can add it back yourself with `formatError`. `error.extensions.exception.stacktrace` is now available on `error.extensions.stacktrace`.

  Provide `unwrapResolverError` function in `@apollo/server/errors`; useful for your `formatError` hook.

  No more TS `declare module` describing the `exception` extension (partially incorrectly).

  Rename the (new in v4) constructor option `includeStackTracesInErrorResponses` to `includeStacktraceInErrorResponses`.

- Updated dependencies [[`bce9150f3`](https://github.com/apollographql/apollo-server/commit/bce9150f31d6fd58b7a6622611ec7b35b3564aa6), [`c4115e96a`](https://github.com/apollographql/apollo-server/commit/c4115e96ac75e04cffe1c3353fc03ea65dcab909), [`6ef6a090c`](https://github.com/apollographql/apollo-server/commit/6ef6a090cff26f5d98e9965cd839307931e12516), [`536e038a7`](https://github.com/apollographql/apollo-server/commit/536e038a744738f740072781f32e83a360ec0744)]:
  - @apollo/server@4.0.0-alpha.3

## 4.0.0-alpha.2

### Patch Changes

- [#6760](https://github.com/apollographql/apollo-server/pull/6760) [`052f1b548`](https://github.com/apollographql/apollo-server/commit/052f1b548c7f882d4cee1c6730cd15463086af6b) Thanks [@glasser](https://github.com/glasser)! - Relax error-handling expectations to work better with Fastify

- Updated dependencies [[`f736b4980`](https://github.com/apollographql/apollo-server/commit/f736b4980b39f3b563939b100eff85e073189cb1)]:
  - @apollo/server@4.0.0-alpha.2

## 4.0.0-alpha.1

### Patch Changes

- [#6357](https://github.com/apollographql/apollo-server/pull/6357) [`7c3c825d8`](https://github.com/apollographql/apollo-server/commit/7c3c825d834ddad778de8b6d4254e56613fe8534) Thanks [@trevor-scheer](https://github.com/trevor-scheer)! - Export ApolloServerErrorCode enum instead of error classes. HTTPGraphQLRequest takes search params as raw string.

- Updated dependencies [[`7c3c825d8`](https://github.com/apollographql/apollo-server/commit/7c3c825d834ddad778de8b6d4254e56613fe8534)]:
  - @apollo/server@4.0.0-alpha.1
  - @apollo/usage-reporting-protobuf@4.0.0-alpha.1

## 4.0.0-alpha.0

### Major Changes

- [`f39d9eec7`](https://github.com/apollographql/apollo-server/commit/f39d9eec7ab72d0f471a0bb0646dd42ad81c56cf) Thanks [@glasser](https://github.com/glasser)! - Initial Apollo Server 4 release

### Patch Changes

- Updated dependencies [[`f39d9eec7`](https://github.com/apollographql/apollo-server/commit/f39d9eec7ab72d0f471a0bb0646dd42ad81c56cf)]:
  - @apollo/server@4.0.0-alpha.0
  - @apollo/usage-reporting-protobuf@4.0.0-alpha.0