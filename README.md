# Dongoose

Dongoose is a simple ( but intelligent ), lightweight, and easy to use ORM for Deno KV. It is written in Typescript and is inspired by Mongoose.

## Features

- 📄 **Schema** - Dongoose leverages Zod for easy data structuring and validation through a simple schema API.
- 🔍 **Indexes** - Dongoose enables automatic data insertion, update, and deletion through defined indexes.
- ✔️ **Validation** - Dongoose validates data before inserting or updating it using Zod.
- ⏰ **Timestamps** - Dongoose automatically adds timestamps to your data ( createdAt, updatedAt ).
- 📝 **Typescript** - Dongoose is written in Typescript and provides type definitions for all of its methods.
- 🍃 **Lightweight** - Dongoose is very lightweight and has no dependencies other than Zod.
- 👍 **Easy to use** - Dongoose is very easy to use and has a simple API.
- 💯 **Coverage** - Dongoose has 100% test coverage.

### Coming soon

- 🔗 **Relations** - Dongoose will soon support relations between collections.
- 🪝 **Hooks** - Dongoose will soon support hooks for pre and post operations.
- 💰 **Transactions** - Dongoose will soon support transactions.
- ➕ **More** - Dongoose will soon support more features.

## Usage

```typescript
import { d, Dongoose } from "https://deno.land/x/dongoose/mod.ts";

const db = await Deno.openKv();
const users = Dongoose(
  {
    email: d.string().email(),

    username: d.string(),
    password: d.string().min(8).max(32),

    firstname: d.string().optional(),
    lastname: d.string().optional(),
  },
  {
    db,
    name: "users",
    indexes: ["email", "username"],
  }
);

await users.create({
  email: "wugro@jo.st",
  username: "Emmet",
  password: "Homenick",
});

const user = await users.findOne({ email: "zuhkopu@rel.edu" });
const _sameUserWithId = await users.findById(user!.id);

await users.updateById(user.id, { firstname: "John" });

await users.deleteById(user.id);
```

## API

### Dongoose

```typescript
Dongoose(schema, options);
```

#### options

```typescript
{
  db: KVStore;
  name: string;
  indexes?: string[];
}
```

### create

```typescript
await users.create({
  email: "malcatbo@wulvi.com",
  username: "Emmet",
});
```

### findOne

```typescript
await users.findOne({ email: "malcatbo@wulvi.com" });
```

### findById

```typescript
await users.findById("076520f1-cbf1-4e29-8af5-d6db8c851371");
```

### updateOne

```typescript
await users.updateOne({ username: "Emmet" });
```

### updateById

```typescript
await users.updateById("076520f1-cbf1-4e29-8af5-d6db8c851371", {
  username: "garrett.guzman",
});
```

### deleteOne

```typescript
await users.deleteOne({ username: "Emmet" });
```

### deleteById

```typescript
await users.deleteById("076520f1-cbf1-4e29-8af5-d6db8c851371");
```

## License

Dongoose is licensed under the MIT license. See [LICENSE](LICENSE) for more information.
