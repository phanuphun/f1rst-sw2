# F1rst-SW2

A TypeScript wrapper library for SweetAlert2 that provides simplified and customizable alert, toast, and confirmation dialogs.

## Features

- 🎨 **Beautiful Alerts** - Default styled alert messages
- 🍞 **Toast Notifications** - Non-intrusive toast messages  
- ✅ **Confirmation Dialogs** - Customizable confirmation prompts
- 🖼️ **Light Box** - Image preview modal
- 🎯 **TypeScript Support** - Full TypeScript type definitions
- ⚙️ **Highly Configurable** - Extensive customization options

## Installation

```shell
npm i f1rst-sw2
```

## Quick Start

```typescript
import MsgAlert from 'f1rst-sw2'

const msgAlert = new MsgAlert()

// Simple alert
msgAlert.default_msg({ 
    title: 'Success!', 
    msg: 'Operation completed successfully',
    icon: 'success' 
})

// Toast notification
msgAlert.toast_msg({ 
    title: 'Hello World!', 
    icon: 'success' 
})

// Confirmation dialog
const result = await msgAlert.confirm('Are you sure?')
if (result) {
    console.log('User confirmed')
}

// Light box for images
msgAlert.lightBox('https://example.com/image.jpg', '800px')
```

## API Reference

### MsgOption Interface

```typescript
interface msgOption {
    title: string;           // Alert title (required)
    msg?: string;           // Alert message
    icon?: SweetAlertIcon;  // 'success' | 'error' | 'warning' | 'info' | 'question'
    position?: SweetAlertPosition; // Alert position
    confirmBtn?: boolean;   // Show confirm button
    cancelBtn?: boolean;    // Show cancel button
    closeBtn?: boolean;     // Show close button
    confirmText?: string;   // Custom confirm button text
    cancelText?: string;    // Custom cancel button text
    timer?: number;         // Auto close timer (seconds)
    progressbar?: boolean;  // Show timer progress bar
    width?: string;         // Custom width
}
```

### Methods

#### `default_msg(option: msgOption)`

Display a standard alert dialog.

```typescript
msgAlert.default_msg({
    title: 'Welcome!',
    msg: 'This is a default alert message',
    icon: 'info',
    position: 'center',
    confirmBtn: true,
    cancelBtn: false,
    timer: 5, // 5 seconds
    progressbar: true
})
```

#### `toast_msg(option: msgOption)`

Display a toast notification with colored background based on icon type.

```typescript
msgAlert.toast_msg({
    title: 'File saved!',
    msg: 'Your changes have been saved successfully',
    icon: 'success',
    position: 'bottom-end',
    timer: 3,
    width: '300px'
})
```

**Toast Colors:**
- `success` - Green (#22c55e)
- `error` - Red (#ef4444)
- `warning` - Yellow (#eab308)
- `info` - Cyan (#06b6d4)
- `question` - Gray (#64748b)

#### `confirm(msg: string, icon?: SweetAlertIcon, showCancelButton?: boolean, confirmButtonText?: string)`

Display a confirmation dialog and return a Promise.

```typescript
// Basic confirmation
const result = await msgAlert.confirm('Delete this item?')

// Custom confirmation
const result = await msgAlert.confirm(
    'Are you sure you want to proceed?',
    'warning',
    true,
    'Yes, proceed'
)

if (result) {
    // User confirmed
    console.log('Action confirmed')
}
```

#### `lightBox(url: string, width?: string)`

Display an image in a modal light box.

```typescript
// Default width (600px)
msgAlert.lightBox('https://example.com/image.jpg')

// Custom width
msgAlert.lightBox('https://example.com/image.jpg', '1200px')
```

## Examples

### Success Notification

```typescript
msgAlert.default_msg({
    title: 'Success!',
    msg: 'Data saved successfully',
    icon: 'success',
    timer: 3,
    progressbar: true
})
```

### Error Alert

```typescript
msgAlert.default_msg({
    title: 'Error!',
    msg: 'Something went wrong',
    icon: 'error',
    confirmBtn: true,
    confirmText: 'Try Again'
})
```

### Custom Toast

```typescript
msgAlert.toast_msg({
    title: 'New Message',
    msg: 'You have a new notification',
    icon: 'info',
    position: 'top-end',
    timer: 5,
    width: '350px'
})
```

### Async Confirmation

```typescript
async function deleteItem(id: number) {
    const confirmed = await msgAlert.confirm(
        'This action cannot be undone. Continue?',
        'warning',
        true,
        'Delete'
    )
    
    if (confirmed) {
        // Proceed with deletion
        console.log(`Deleting item ${id}`)
    }
}
```

## Position Options

- `top`, `top-start`, `top-end`
- `center`, `center-start`, `center-end`  
- `bottom`, `bottom-start`, `bottom-end`

## Icon Types

- `success` - Green checkmark
- `error` - Red X
- `warning` - Yellow exclamation
- `info` - Blue information
- `question` - Gray question mark

## Dependencies

- [SweetAlert2](https://sweetalert2.github.io/) ^11.15.2

## License

ISC

## Author

phanuphun

## Repository

[GitHub](https://github.com/phanuphun/f1rst-sw2)
