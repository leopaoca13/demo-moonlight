# Moonlight API Integration

This document outlines how to integrate the Moonlight API in your frontend application using the Tauri backend.

## Overview

The Moonlight API allows you to establish a connection to a remote computer for streaming purposes. The API provides several functions to start and manage the streaming session.

## Prerequisites

- Ensure you have Tauri set up in your project.
- The backend should be running and accessible.

## API Functions

### 1. Start Moonlight Streaming

To start a Moonlight streaming session, use the `StartMoonlight` function.

#### Function Signature
```typescript
async function StartMoonlight(
    computer: Computer,
    options?: MoonlightStreamConfig,
    callback?: (type: 'stdout' | 'stderr', log: string) => void
): Promise<MoonlightStream>
```

#### Parameters

- `computer`: An object of type `Computer` containing the address of the remote machine.
- `options` (optional): Configuration options for the stream, including:
  - `bitrate`: The bitrate of the stream (default: 6000).
  - `width`: The width of the stream (default: 1920).
  - `height`: The height of the stream (default: 1080).
- `callback` (optional): A function to handle logs from the Moonlight process.

#### Example Usage
```javascript
const computer = { address: '192.168.1.100' }; // Replace with your computer's address which running daemon
 options = { bitrate: 8000, width: 1280, height: 720 };
StartMoonlight(computer, options, (type, log) => {
    console.log([${type}] ${log});
}).then(stream => {
    console.log('Moonlight streaming started:', stream);
}).catch(error => {
    console.error('Error starting Moonlight:', error);
});
```
### 2. Close Moonlight Streaming

To close an active Moonlight streaming session, use the `CloseMoonlight` function.

#### Function Signature
```typescript
async function CloseMoonlight(stream: MoonlightStream): Promise<Error | 'SUCCESS'>
```
#### Parameters

- `stream`: The `MoonlightStream` object returned from `StartMoonlight`.

#### Example Usage

```javascript
CloseMoonlight(stream).then(result => {
    console.log('Moonlight streaming closed:', result);
}).catch(error => {
    console.error('Error closing Moonlight:', error);
});
```
