---
title: Next.js
---

```ts title="pages/api/someQueue.ts"
import { Queue } from "quirrel/next";

export default Queue(
"api/someQueue",
  async (job, meta) => {
    // do something
  }
);
```

Creates a new Queue.
Make sure to export it from an [API Route](https://nextjs.org/docs/api-routes/introduction), otherwise it won't work.

#### Parameters

```ts
function Queue<T>(
  path: string,
  worker: (job: T, meta: JobMeta): Promise<void>,
  defaultJobOptions?: { exclusive?: boolean }
): QueueInstance<T>
```

| Parameter           | Usage                                                           |
| ------------------- | --------------------------------------------------------------- |
| `path`              | The route that this queue is reachable at.                      |
| `worker`            | a function that takes the job's payload and returns a `Promise` |
| `defaultJobOptions` | Optional. Use to set default options applied to every job.      |
