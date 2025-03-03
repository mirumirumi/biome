---
title: noEmptyCharacterClassInRegex (since vnext)
---

**Diagnostic Category: `lint/nursery/noEmptyCharacterClassInRegex`**

:::caution
This rule is part of the [nursery](/linter/rules/#nursery) group.
:::

Disallow empty character classes in regular expression literals.

Empty character classes don't match anything.
In contrast, negated empty classes match any character.
They are often the result of a typing mistake.

Source: https://eslint.org/docs/latest/rules/no-empty-character-class/

## Examples

### Invalid

```jsx
/^a[]/.test("a"); // false
```

<pre class="language-text"><code class="language-text">nursery/noEmptyCharacterClassInRegex.js:1:4 <a href="https://biomejs.dev/lint/rules/no-empty-character-class-in-regex">lint/nursery/noEmptyCharacterClassInRegex</a> ━━━━━━━━━━━━━━

<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">✖</span></strong> <span style="color: Tomato;">The regular expression includes this </span><span style="color: Tomato;"><strong>empty character class</strong></span><span style="color: Tomato;">.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>/^a[]/.test(&quot;a&quot;); // false
   <strong>   │ </strong>   <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>2 │ </strong>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Empty character classes don't match anything.
</span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">If you want to match against </span><span style="color: rgb(38, 148, 255);"><strong>[</strong></span><span style="color: rgb(38, 148, 255);">, escape it </span><span style="color: rgb(38, 148, 255);"><strong>\[</strong></span><span style="color: rgb(38, 148, 255);">.
</span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">Otherwise, remove the character class or fill it.</span>
  
</code></pre>

```jsx
/^a[^]/.test("ax"); // true
```

<pre class="language-text"><code class="language-text">nursery/noEmptyCharacterClassInRegex.js:1:4 <a href="https://biomejs.dev/lint/rules/no-empty-character-class-in-regex">lint/nursery/noEmptyCharacterClassInRegex</a> ━━━━━━━━━━━━━━

<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">✖</span></strong> <span style="color: Tomato;">The regular expression includes this </span><span style="color: Tomato;"><strong>negated empty character class</strong></span><span style="color: Tomato;">.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>/^a[^]/.test(&quot;ax&quot;); // true
   <strong>   │ </strong>   <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>2 │ </strong>
  
<strong><span style="color: rgb(38, 148, 255);">  </span></strong><strong><span style="color: rgb(38, 148, 255);">ℹ</span></strong> <span style="color: rgb(38, 148, 255);">Negated empty character classes match anything.
</span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">If you want to match against </span><span style="color: rgb(38, 148, 255);"><strong>[</strong></span><span style="color: rgb(38, 148, 255);">, escape it </span><span style="color: rgb(38, 148, 255);"><strong>\[</strong></span><span style="color: rgb(38, 148, 255);">.
</span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">  </span><span style="color: rgb(38, 148, 255);">Otherwise, remove the character class or fill it.</span>
  
</code></pre>

## Valid

```jsx
/^a[xy]/.test("ay"); // true
```

```jsx
/^a[^xy]/.test("ab"); // true
```

```jsx
/^a\[]/.test("a[]"); // true
```

## Related links

- [Disable a rule](/linter/#disable-a-lint-rule)
- [Rule options](/linter/#rule-options)
