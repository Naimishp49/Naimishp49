# Components Documentation Guide

Use consistent component docs to improve discoverability and reuse.

## What to Include
- Purpose: When to use the component
- Props API: Name, type, default, description
- Examples: Minimal usage snippets
- Accessibility: Keyboard, ARIA, focus behavior
- States: Loading, empty, error, interactive states

## Template (React/TypeScript)
```tsx
/** Button that emphasizes primary actions. */
export type ButtonProps = {
	label: string;
	onClick?: () => void;
	disabled?: boolean;
	variant?: "primary" | "secondary" | "ghost";
};

export function Button({ label, onClick, disabled, variant = "primary" }: ButtonProps) {
	const className = `btn btn-${variant}` + (disabled ? " btn-disabled" : "");
	return (
		<button className={className} onClick={onClick} disabled={disabled}>
			{label}
		</button>
	);
}
```

### Usage
```tsx
<Button label="Save" variant="primary" onClick={() => console.log("saved")} />
<Button label="Cancel" variant="secondary" />
<Button label="Delete" variant="ghost" disabled />
```

### Accessibility
- Ensure focus ring is visible
- Provide `aria-disabled` when appropriate
- Label reflects action clearly

### Visual States
- Hover, focus, active
- Disabled
- Loading spinner (if applicable)