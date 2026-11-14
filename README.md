# Clautzy Shell MCP Server

MCP (Model Context Protocol) server sederhana berbasis Node.js dan Express yang menyediakan kemampuan eksekusi perintah shell (`execute_command`) melalui protokol Model Context Protocol dengan dukungan SSE (Server-Sent Events).

## Fitur
- **Eksekusi Perintah Shell**: Memungkinkan klien MCP untuk menjalankan perintah sistem melalui tool `execute_command`.
- **SSE (Server-Sent Events)**: Mendukung komunikasi real-time menggunakan transport SSE.
- **Manajemen Proses PM2**: Dijalankan di background menggunakan PM2.
- **Ngrok Tunnel**: Terhubung ke publik secara aman melalui Ngrok.

---

## Konfigurasi & Endpoint

- **Port Lokal**: `8181`
- **Endpoint SSE**: `/sse`
- **Endpoint Pesan POST**: `/messages`
- **Public URL Ngrok (Aktif)**: `https://middlemost-forensically-cody.ngrok-free.dev/sse`

---

## Cara Instalasi & Menjalankan (Lokal)

1. Clone atau masuk ke direktori `MCP_SERVER`.
2. Install dependensi:
   ```bash
   npm install
   ```
3. Jalankan server secara manual:
   ```bash
   npm start
   ```

---

## Menjalankan dengan PM2 & Ngrok

1. **Jalankan via PM2**:
   ```bash
   pm2 start index.js --name "mcp-server-8181"
   pm2 save
   ```

2. **Setup Authtoken Ngrok & Buka Tunnel**:
   ```bash
   ngrok config add-authtoken <YOUR_NGROK_AUTHTOKEN>
   ngrok http 8181
   ```

---

## Daftar Tools MCP

### `execute_command`
Menjalankan perintah shell di sistem server.

- **Input Schema**:
  ```json
  {
    "type": "object",
    "properties": {
      "command": {
        "type": "string",
        "description": "Perintah shell yang ingin dieksekusi"
      }
    },
    "required": ["command"]
  }
  ```
