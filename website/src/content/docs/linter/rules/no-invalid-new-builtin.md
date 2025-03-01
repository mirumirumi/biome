---
title: noInvalidNewBuiltin (since vnext)
---

**Diagnostic Category: `lint/nursery/noInvalidNewBuiltin`**

:::caution
This rule is part of the [nursery](/linter/rules/#nursery) group.
:::

Disallow `new` operators with global non-constructor functions.

Some global functions cannot be called using the new operator and
will throw a `TypeError` if you attempt to do so. These functions are:

- [`Symbol`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol/Symbol)
- [`BigInt`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/BigInt/BigInt)

Source: https://eslint.org/docs/latest/rules/no-new-native-nonconstructor/

## Examples

### Invalid

```jsx
let foo = new Symbol('foo');
```

<pre class="language-text"><code class="language-text">nursery/noInvalidNewBuiltin.js:1:11 <a href="https://biomejs.dev/lint/rules/no-invalid-new-builtin">lint/nursery/noInvalidNewBuiltin</a> <span style="color: #000; background-color: #ddd;"> FIXABLE </span> ━━━━━━━━━━━━━━━━━━━━━

<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">✖</span></strong> <span style="color: Tomato;"><strong>Symbol</strong></span><span style="color: Tomato;"> cannot be called as a constructor.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>let foo = new Symbol('foo');
   <strong>   │ </strong>          <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>2 │ </strong>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Calling </span><span style="color: rgb(38, 148, 255);"><strong>Symbol</strong></span><span style="color: rgb(38, 148, 255);"> with the </span><span style="color: rgb(38, 148, 255);"><strong>new</strong></span><span style="color: rgb(38, 148, 255);"> operator throws a </span><span style="color: rgb(38, 148, 255);"><strong>TypeError</strong></span><span style="color: rgb(38, 148, 255);">.</span>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Unsafe fix</span><span style="color: rgb(38, 148, 255);">: </span><span style="color: rgb(38, 148, 255);">Remove </span><span style="color: rgb(38, 148, 255);"><strong>new</strong></span><span style="color: rgb(38, 148, 255);">.</span>
  
<strong>  </strong><strong>  1 │ </strong>let<span style="opacity: 0.8;">·</span>foo<span style="opacity: 0.8;">·</span>=<span style="opacity: 0.8;">·</span><span style="color: Tomato;">n</span><span style="color: Tomato;">e</span><span style="color: Tomato;">w</span><span style="opacity: 0.8;"><span style="color: Tomato;">·</span></span>Symbol('foo');
<strong>  </strong><strong>    │ </strong>          <span style="color: Tomato;">-</span><span style="color: Tomato;">-</span><span style="color: Tomato;">-</span><span style="color: Tomato;">-</span>              
</code></pre>

```jsx
let bar = new BigInt(9007199254740991);
```

<pre class="language-text"><code class="language-text">nursery/noInvalidNewBuiltin.js:1:11 <a href="https://biomejs.dev/lint/rules/no-invalid-new-builtin">lint/nursery/noInvalidNewBuiltin</a> <span style="color: #000; background-color: #ddd;"> FIXABLE </span> ━━━━━━━━━━━━━━━━━━━━━

<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">✖</span></strong> <span style="color: Tomato;"><strong>BigInt</strong></span><span style="color: Tomato;"> cannot be called as a constructor.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>let bar = new BigInt(9007199254740991);
   <strong>   │ </strong>          <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>2 │ </strong>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Calling </span><span style="color: rgb(38, 148, 255);"><strong>BigInt</strong></span><span style="color: rgb(38, 148, 255);"> with the </span><span style="color: rgb(38, 148, 255);"><strong>new</strong></span><span style="color: rgb(38, 148, 255);"> operator throws a </span><span style="color: rgb(38, 148, 255);"><strong>TypeError</strong></span><span style="color: rgb(38, 148, 255);">.</span>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Unsafe fix</span><span style="color: rgb(38, 148, 255);">: </span><span style="color: rgb(38, 148, 255);">Remove </span><span style="color: rgb(38, 148, 255);"><strong>new</strong></span><span style="color: rgb(38, 148, 255);">.</span>
  
<strong>  </strong><strong>  1 │ </strong>let<span style="opacity: 0.8;">·</span>bar<span style="opacity: 0.8;">·</span>=<span style="opacity: 0.8;">·</span><span style="color: Tomato;">n</span><span style="color: Tomato;">e</span><span style="color: Tomato;">w</span><span style="opacity: 0.8;"><span style="color: Tomato;">·</span></span>BigInt(9007199254740991);
<strong>  </strong><strong>    │ </strong>          <span style="color: Tomato;">-</span><span style="color: Tomato;">-</span><span style="color: Tomato;">-</span><span style="color: Tomato;">-</span>                         
</code></pre>

## Valid

```jsx
let foo = Symbol('foo');

function baz(Symbol) {
    const qux = new Symbol("baz");
}
```

```jsx
let bar = BigInt(9007199254740991);

function quux(BigInt) {
    const corge = new BigInt(9007199254740991);
}
```

## Related links

- [Disable a rule](/linter/#disable-a-lint-rule)
- [Rule options](/linter/#rule-options)
