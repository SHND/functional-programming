## Question

Is the following semigroup instance lawful (does it respect semigroup laws)?

```ts
import { Semigroup } from 'fp-ts/Semigroup'

/** Always return the last argument */
const last = <A>(): Semigroup<A> => ({
  concat: (_first, second) => second
})
```

## Answer

Yes:

- `first`, `second` and the result of `concat` (which is `first`) are all of the same type `A`
- `concat` is associative:
  - `concat(concat(first, second), third)` evaluates to `concat(first, third)` which then evaluates to `first`
  - `concat(first, concat(second, third))` evaluates to `concat(first, second)` which then evaluates to `first`
