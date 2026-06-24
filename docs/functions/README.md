# Functions Documentation Guide

Document functions to make their intent, inputs, and outputs clear.

## What to Include
- Purpose: What problem the function solves
- Signature: Parameters and return type
- Behavior: Side effects, error cases
- Examples: Minimal usage demonstrating typical and edge cases

## Template (JSDoc-style)
```ts
/**
 * <Short description>
 *
 * @param paramA - <description>
 * @param paramB - <description>
 * @returns <description>
 * @throws <ErrorType> when <condition>
 * @example
 * const result = myFunction("input");
 * console.log(result);
 */
export function myFunction(paramA: string, paramB?: number): string {
	// implementation
	return `${paramA}-${paramB ?? 0}`;
}
```

## Example: Input Validation Utility
```ts
/** Checks if a string is a valid UUID v4. */
export function isUuidV4(value: string): boolean {
	const uuidV4Regex = /^[0-9a-f]{8}-[0-9a-f]{4}-4[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$/i;
	return uuidV4Regex.test(value);
}

// Usage
if (!isUuidV4(userId)) {
	throw new Error("Invalid user id");
}
```

## Example: Async Function with Errors
```ts
/** Fetches user by id; throws if not found. */
export async function fetchUser(userId: string): Promise<User> {
	const response = await fetch(`/api/users/${userId}`);
	if (!response.ok) {
		throw new Error(`User ${userId} not found`);
	}
	return response.json();
}

// Usage with try/catch
try {
	const user = await fetchUser("123");
	console.log(user.name);
} catch (error) {
	console.error("Failed to fetch user", error);
}
```

## Writing Good Examples
- Keep examples runnable and minimal
- Show typical case, error case, and edge case when relevant
- Prefer TypeScript/typed languages for clarity