# XYRE Wallet

A simple self-custody XRP Ledger wallet built with React, Vite, and `xrpl.js`.

## Mainnet only

This edition connects only to **XRP Ledger Mainnet**. There is no Testnet switch and no faucet. Any XRP you send is real XRP.

## Features

- Create a new XRP Ledger wallet
- Import an existing XRPL recovery seed
- View Mainnet XRP balance
- Send XRP with optional destination tag
- Receive XRP with QR code
- Download recovery seed, private key, or full recovery kit
- Wallet secrets stay in browser memory only
- Mainnet server fallback for better availability
- One-click local launchers for Windows, macOS, and Linux
- One-click production builders for Windows, macOS, and Linux
- Deploy-ready `dist/` and packaged web release

## Requirement

Install **Node.js 20.19+**. Node.js 22 LTS is recommended.

## One-click local launch

### Windows
Double-click:

`RUN-WINDOWS.bat`

### macOS
Double-click:

`RUN-MAC.command`

If macOS blocks it the first time, right-click the file and choose **Open**.

### Linux
Double-click `RUN-LINUX.desktop` where supported, or run:

`RUN-LINUX.sh`

The local launcher installs dependencies when needed, builds the wallet, starts a localhost-only server, chooses an available port starting at 5173, and opens your default browser automatically.

## One-click production build

Use these when you want a build that can be uploaded to a website.

### Windows
Double-click:

`BUILD-PRODUCTION-WINDOWS.bat`

### macOS
Double-click:

`BUILD-PRODUCTION-MAC.command`

### Linux
Double-click `BUILD-PRODUCTION-LINUX.desktop` where supported, or run:

`BUILD-PRODUCTION-LINUX.sh`

The builder automatically:

1. Checks that a supported Node.js version is installed.
2. Installs/updates npm dependencies.
3. Runs an optimized Vite production build.
4. Creates `dist/`.
5. Creates `release/xyre-wallet-web/`.
6. Creates `release/xyre-wallet-web.zip`.
7. Opens the `release/` folder when supported.

The generated web build is platform-independent. The same ZIP can be built on Windows, macOS, or Linux and deployed to a static web host.

## Manual production build

```bash
npm install --include=optional
npm run release
```

Production outputs:

```text
dist/
release/
├── xyre-wallet-web/
└── xyre-wallet-web.zip
```

For most static hosting providers, upload the **contents** of `release/xyre-wallet-web/` or extract `xyre-wallet-web.zip` at the website root.

## Manual local launch

```bash
npm install --include=optional
npm run start
```

The local wallet runs only on `127.0.0.1`. It starts at port `5173` and automatically tries the next port if that one is already in use.

## Security notes

- This is a self-custody wallet: anyone with the recovery seed or private key controls the XRP.
- Do not share recovery files.
- Keep offline backups.
- The app intentionally does not save wallet secrets to `localStorage` or a database.
- Closing/reloading the wallet clears the in-memory wallet session.
- Mainnet means real funds. Verify address, amount, and destination tag before sending.
- If you publish this wallet on the web, use HTTPS and avoid third-party scripts that could access wallet secrets.
- A publicly hosted Mainnet wallet should receive a professional security review before handling significant funds.

## Mainnet connectivity

The app tries these public Mainnet WebSocket servers in order:

1. `wss://xrplcluster.com/`
2. `wss://s1.ripple.com/`
3. `wss://s2.ripple.com/`

For a high-value or production deployment, use infrastructure you operate or trust rather than relying only on public endpoints.
