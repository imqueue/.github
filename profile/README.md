<div align="center">

<a href="https://imqueue.org"><img src="https://imqueue.org/images/og-org.png" alt="@imqueue — RPC over a message queue for Node.js & TypeScript" width="640"></a>

### RPC over a message queue for Node.js &amp; TypeScript

Build message-driven microservices that call each other like local objects — **no HTTP layer, no gRPC, no schema files**. Just decorated TypeScript classes over a Redis-backed message queue, with generated, fully-typed clients.

[**Documentation → imqueue.org**](https://imqueue.org) · [**Commercial licensing → imqueue.com**](https://imqueue.com) · [**Get started**](https://imqueue.org/get-started/) · [**Blog**](https://imqueue.org/blog/)

</div>

---

## Why @imqueue

- **Type-safe service-to-service RPC.** Expose a method with a decorator; the CLI generates a fully-typed client. Types flow across the network boundary — no hand-written clients, no drift.
- **No HTTP boilerplate.** Services communicate over a message queue (Redis today), so you get competing-consumer load balancing and back-pressure for free — no load balancer, no service mesh required.
- **Guaranteed & delayed delivery, built in.** Safe delivery, retries, and millisecond-precision scheduling are first-class across the framework.
- **TypeScript-first, decorator-driven.** JSDoc is the source of truth for types — no `reflect-metadata`, no separate IDL.

```bash
npm i @imqueue/rpc
npm i -g @imqueue/cli   # scaffolding & typed-client generation
```

```ts
import { IMQService, expose } from '@imqueue/rpc';

class UserService extends IMQService {
    @expose()
    public async getUser(id: number): Promise<{ id: number; name: string }> {
        return { id, name: 'Ada' };
    }
}
```

## Packages

| Package | What it is |
|---|---|
| [`@imqueue/rpc`](https://github.com/imqueue/rpc) | Type-safe RPC over a message queue — decorators, services & generated clients |
| [`@imqueue/core`](https://github.com/imqueue/core) | The Redis-backed messaging-queue engine shared by the framework |
| [`@imqueue/cli`](https://github.com/imqueue/cli) | Scaffolding, typed-client generation and local service management |
| [`@imqueue/job`](https://github.com/imqueue/job) | Simple, safe-by-default Redis job queue (delayed/scheduled jobs, retries) |

**Integrations & utilities:** [`pg-cache`](https://github.com/imqueue/pg-cache) · [`pg-pubsub`](https://github.com/imqueue/pg-pubsub) · [`tag-cache`](https://github.com/imqueue/tag-cache) · [`graphql-dependency`](https://github.com/imqueue/graphql-dependency) · [`type-graphql-dependency`](https://github.com/imqueue/type-graphql-dependency) · [`async-logger`](https://github.com/imqueue/async-logger) · [`http-protect`](https://github.com/imqueue/http-protect) · [`dd-trace`](https://github.com/imqueue/dd-trace) · [`opentelemetry-instrumentation-imqueue`](https://github.com/imqueue/opentelemetry-instrumentation-imqueue)

## Using an AI assistant?

@imqueue publishes machine-readable docs for coding agents. Point your assistant at **[imqueue.org/llms.txt](https://imqueue.org/llms.txt)** (or [AGENTS.md](https://github.com/imqueue/rpc/blob/master/AGENTS.md) in each repo) so it generates correct, idiomatic @imqueue code. See the [AI assistants guide](https://imqueue.org/using-ai-assistants/).

## License

@imqueue is open source under **GPL-3.0**. Shipping inside a closed-source product? A **commercial license** is available — see [imqueue.com](https://imqueue.com) and the [licensing explainer](https://imqueue.org/license/). Contributions are welcome — see [CONTRIBUTING](https://github.com/imqueue/.github/blob/master/CONTRIBUTING.md).
