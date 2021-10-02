# Some Typescript tips 

### Custom Types
```ts
// In TypeScript you can create your own custom types with type keyword
type fontFamily = "monospace" | "sans" | "san-serif"

// this will parse type of color as string 
export default {
 color : "red",
 fontSize : 12,
 fontFamily : "monospace"
}

// this will parse type of color as "red" and fontFamily as "monospace"
export default {
 color : "red",
 fontSize : 12,
 fontFamily : "monospace"
} as const;

// in typescript 4.1 there is new feature called the template literal types
// where you can combine two custom types. Check more here 
// https://www.typescriptlang.org/docs/handbook/2/template-literal-types.html

```

Moar Soon..
