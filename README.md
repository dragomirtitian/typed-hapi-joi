# EXPERIMENT!
Better types for hapi/joi, read sumary 
# Installation
> `npm install --save https://github.com/dragomirtitian/typed-hapi-joi.git`

# Summary
This package builds on top of existing types from definately typed, but adds the ability to derive typed directly from the schema.
Example usage: 
```ts
import Joi, { SchemaToType } from "@hapi/joi";

export const Status = Joi.string().valid("open", "closed", "publish");
type Status  =  SchemaToType<typeof Status> // will be "open" | "closed" | "publish"

export const HtmlContent = Joi.object({
    rendered: Joi.string().required(),
    protected: Joi.bool().optional()
}).required().label("HtmlContent")
export interface HtmlContent extends SchemaToType<typeof HtmlContent> { }
// Same as
// {
//     rendered: string;
//     protected?: boolean | undefined;
// }
```
You can also use a type alias `type HtmlContent = SchemaToType<typeof HtmlContent>` but that will cause expansion of the type in errors (a big problem for large types). Interfaces will provide stronger names for the compiler to use.

## Curently supported for type extraction
- `Schema.required` - property will be reuired in the type
- `Schema.exist` - property will be required in the type
- `Schema.optional` - property will be optional in the type
- `Schema.forbidden` - property will be present and typed as undefined
- `Schema.presence` - property will respect the presence provided
- `Schema.allow` - will only affect the type if `only` is also specified. If only is specified will preserve the literal values as a union to be used as the property type
- `Schema.valid` - property will be typed as a union of values specified. same as `allow(...).only()`
- `Joi.object` - will preseve keys with apropriate types
- `Joi.alternatives` - will craete a union of the types of the provided schemas
- `Array.items` - will type the array as having items of the specfied type
- `Array.ordered` - will create the type as a tuple with the specified items




# Details
Files were exported from https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/hapi__joi.

### Additional Details
 * Last updated: Tue, 02 Jun 2020 15:48:01 GMT
 * Dependencies: none
 * Global values: none

# Credits
These definitions were written by [Bart van der Schoor](https://github.com/Bartvds), [Laurence Dougal Myers](https://github.com/laurence-myers), [Christopher Glantschnig](https://github.com/cglantschnig), [David Broder-Rodgers](https://github.com/DavidBR-SW), [Gael Magnan de Bornier](https://github.com/GaelMagnan), [Rytis Alekna](https://github.com/ralekna), [Pavel Ivanov](https://github.com/schfkt), [Youngrok Kim](https://github.com/rokoroku), [Dan Kraus](https://github.com/dankraus), [Anjun Wang](https://github.com/wanganjun), [Rafael Kallis](https://github.com/rafaelkallis), [Conan Lai](https://github.com/aconanlai), [Peter Thorson](https://github.com/zaphoyd), [Will Garcia](https://github.com/thewillg), [Simon Schick](https://github.com/SimonSchick), [Alejandro Fernandez Haro](https://github.com/afharo), [Silas Rech](https://github.com/lenovouser), [Anand Chowdhary](https://github.com/AnandChowdhary), [Miro Yovchev](https://github.com/myovchev), [David Recuenco](https://github.com/RecuencoJones), [Frederic Reisenhauer](https://github.com/freisenhauer), [Stefan-Gabriel Muscalu](https://github.com/legraphista), [Simcha Wood](https://github.com/SimchaWood), and [Steven Barnett](https://github.com/stevendesu).
