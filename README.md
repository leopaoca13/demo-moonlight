# Demo Moonlight

## Requirements
- Node.js version: **18.19.0** or higher

## Local Development Setup
To run the project locally for development, follow these steps:

1. Initialize git submodules:
   ```bash
   git submodule update --init --recursive
   ```

2. Copy the Tauri configuration file:
   ```bash
   cp ./src-tauri/tauri.conf.vanilla.json ./src-tauri/tauri.conf.json
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Build the project:
   ```bash
   npm run build
   ```

5. Start the development server:
   ```bash
   npm run tauri dev
   ```


## Additional Resources
- Daemon Server source: [Daemon Server GitHub](https://github.com/thinkonmay/binary/blob/groupobright/daemon.exe)