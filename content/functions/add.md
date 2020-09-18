---
title: add function
description: a thorough tour of add function
---

## Add

Adds two numbers

* Curried

**Non curried type declaration**
```typescript
function add(a: number, b: number): number {
  // ...
}
```
<br>

**Curried type declaration**

```typescript
type Add_2 = ((b: number) => number)
  & ((b?: PH) => Add_2)

type Add_1 = ((a: number) => number)
  & ((a?: PH) => Add_1)

type Add = ((a: number, b: number) => number)
  & ((a: number, b?: PH) => Add_2)
  & ((a: PH, b: number) => Add_1)
  & ((a?: PH, b?: PH) => Add)
```
<br>

**Examples**
```typescript
import { add, _ } from 'https://deno.land/x/fae/mod.ts'

add(1, 2)                 // 3
add(1)(2)                 // 3

const add5 = add(5)
add5(-32)                 // -27
add5(_)(12)               // 17
```