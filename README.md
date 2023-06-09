# Generic Condition TypeScript Examples

A set of examples for extends a type by specific condition.

## Type and Interface easily can be extended

Both type are extended into one type.

```typescript
type FullnameType = {
    name: string,
    family: string,
}

type ProfessionType = {
    name: string,
    departmentId: string,
}

type FullDetailType = FullnameType & ProfessionType;
```

## Generic is a way to change a type by our rule!

### Correct Type Definition

```typescript
type DynamicType<T> = {
    value: T
}

const data: DynamicType<number> = {
    value: 123
}
```

### Wrong Type Definition

```typescript
type DynamicType<T> = {
    value: T
}

const data: DynamicType<number> = {
    value: "123"
}
```

The correct type is defined by the passed type, on the other hand, the generic is like an argument in a function which
able a type or interface to get a type as input.

## Extend is the same as an operator by a condition

Passed type of “PersonalityType” and extends Same as the following code.

```typescript
type === "legal" ? OurType : AnotherType
```

### The full type definition

```typescript
type PersonalityType = "legal" | "real";

type DataType<T extends PersonalityType> = {
    username: string;
    password: string;
    workEmail: string;
    phoneNumber: string;
    name: string;
    family: string;
} & PersonalityDataType<T>;

type PersonalityDataType<T extends PersonalityType> = T extends "legal"
    ? {
        companyName: string;
        companyNationalId: string;
    }
    : {
        projectName: string;
        nationalId: string;
    };
```

## Data-driven by type condition

When passed type is “real” the type is extended only “projectName” and “nationalId” fields.

```typescript
const realCustomer: DataType<"real"> = {
    nationalId: "124545",
    name: "John",
    family: "Peterly",
    password: "a!@F%$21##!@ADS",
    phoneNumber: "0921454447",
    projectName: "test",
    workEmail: "info@work.com",
    username: "john",
};
```