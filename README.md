<br />
<p align="center">
<a href="https://music.qier222.com" target="blank">
<img src="images/logo.png" alt="Logo" width="156" height="156">
</a>
<h2 align="center" style="font-weight: 600">YesPlayMusic</h2>

<p align="center">
High-value third-party NetEase Cloud player
<br />
<a href="https://music.qier222.com" target="blank"><strong>🌎 Visit DEMO</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
<a href="#%EF%B8%8F-Install" target="blank"><strong>📦️ Download the installation package</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
<a href="https://t.me/yesplaymusic" target="blank"><strong>💬 Join the discussion group</strong></a>
<br />
<br />
</p>
</p>

[![Library][library-screenshot]](https://music.qier222.com)

## New version
The new 2.0 Alpha test version has been released. Welcome to download it from the [Releases](https://github.com/qier222/YesPlayMusic/releases) page.
The current version will enter maintenance mode. Except for major bug fixes, no new features will be updated.

## ✨ Features

- ✅ Developed with Vue.js
- 🔴 Login with NetEase Cloud account (scan code/mobile phone/email login)
- 📺 Support MV playback
- 📃 Support lyrics display
- 📻 Support private FM/daily recommended songs
- 🚫🤝 No social functions
- 🌎️ Overseas users can play directly (need to log in to NetEase Cloud account)
- 🔐 Support [UnblockNeteaseMusic](https://github.com/UnblockNeteaseMusic/server#Sound source list), automatically use [various sound sources](https://github.com/UnblockNeteaseMusic/server#Sound source list) to replace grayed-out song links (not supported by the web version)
- "Various sound sources" refers to the sound sources enabled by default.
- YouTube sound sources need to install `yt-dlp` by themselves.
- ✔️ Daily automatic sign-in (sign-in on both mobile and computer)
- 🌚 Automatic switching between Light/Dark Mode
- 👆 Support Touch Bar
- 🖥️ Support PWA, you can click ➕ on the right side of the address bar in Chrome/Edge to install it on your computer
- 🟥 Support Last.fm Scrobble
- ☁️ Support Music Cloud Drive
- ⌨️ Custom shortcuts and global shortcuts
- 🎧 Support Mpris
- 🛠 More features are being developed

## 📦️ Installation

The Electron version is adapted and maintained by [@hawtim](https://github.com/hawtim) and [@qier222](https://github.com/qier222), and supports macOS, Windows, and Linux.

Visit the [Releases](https://github.com/qier222/YesPlayMusic/releases)
page of this project to download the installation package.

- macOS users can install it through Homebrew: `brew install --cask yesplaymusic`

- Windows users can install it through Scoop: `scoop install extras/yesplaymusic`

## ⚙️ Deploy to Vercel

In addition to downloading the installation package, you can also deploy this project to Vercel or your server. Here is how to deploy to Vercel.

The Demo (https://music.qier222.com) of this project is a website deployed on Vercel.

[![Powered by Vercel](https://www.datocms-assets.com/31049/1618983297-powered-by-vercel.svg)](https://vercel.com/?utm_source=ohmusic&utm_campaign=oss)

1. Deploy the Netease Cloud API. For details, see [Binaryify/NeteaseCloudMusicApi](https://neteasecloudmusicapi.vercel.app/#/?id=%e5%ae%89%e8%a3%85)
. You can also deploy the API to Vercel.

2. Click Fork in the upper right corner of this repository and copy this repository to your GitHub account.

3. Click Add File in the repository, select Create new file, enter `vercel.json`, copy and paste the following content into the file, and replace `https://your-netease-api.example.com` with the NetEase Cloud API address you just deployed:

```json
{
"rewrites": [
{
"source": "/api/:match*",
"destination": "https://your-netease-api.example.com/:match*"
}
]
}
```

4. Open [Vercel.com](https://vercel.com) and log in with GitHub.

5. Click Import Git Repository and select the repository you just copied and click Import.

6. Click Select next to PERSONAL ACCOUNT.

7. Click Environment Variables, fill in Name as `VUE_APP_NETEASE_API_URL`, Value as `/api`, and click Add. Finally, click Deploy at the bottom to deploy to
Vercel.

## ⚙️ Deploy to your own server

In addition to deploying to Vercel, you can also deploy to your own server

1. Deploy Netease Cloud API, see [Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi) for details

2. Clone this repository

```sh
git clone --recursive https://github.com/qier222/YesPlayMusic.git
```

3. Install dependencies

```sh
yarn install

```

4. (Optional) Use Nginx reverse proxy API and map the API path to `/api`. If the API and the web page are not in the same domain name (cross-domain), there will be some bugs.

5. Copy the `/.env.example` file to `/.env`, and modify the value of `VUE_APP_NETEASE_API_URL` to the NetEase Cloud API address. For local development, you can fill in the API address as `http://localhost:3000`, and the YesPlayMusic address as `http://localhost:8080`. If you use a reverse proxy API, you can fill in the API address as `/api`.

```
VUE_APP_NETEASE_API_URL=http://localhost:3000
```

6. Compile and package

```sh
yarn run build
```

7. Upload the files in the `/dist` directory to your web server

## ⚙️ Docker deployment

1. Build Docker Image

```sh
docker build -t yesplaymusic .
```

2. Start Docker Container

```sh
docker run -d --name YesPlayMusic -p 80:80 yesplaymusic
```

3. Start Docker Compose

```sh
docker-compose up -d
```

YesPlayMusic address is `http://localhost`

## ⚙️ Deploy to Replit

1. Create a new Repl and select the Bash template

2. In the Replit shell Run the following command in

```sh
bash <(curl -s -L https://raw.githubusercontent.com/qier222/YesPlayMusic/main/install-replit.sh)
```

3. After the first run is successful, just click the green button `Run` to run it again

4. Since the memory limit of replit personal version is 1G (educational version is 3G), the build process may fail. Please run the above command again or run the following command:

```sh
cd /home/runner/${REPL_SLUG}/music && yarn install && yarn run build
```

## 👷‍♂️ Package the client

If you can't find the installation package for your device on the Release page, you can package your own client according to the steps below.

1. Node.js and Yarn are required to package Electron. You can go to [Node.js official website](https://nodejs.org/zh-cn/) to download the installation package. Install Node.js
After that, you can run `npm install -g yarn` in the terminal to install Yarn.

2. Use `git clone --recursive https://github.com/qier222/YesPlayMusic.git` to clone this repository locally.

3. Use `yarn install` to install project dependencies.

4. Copy the `/.env.example` file to `/.env`.

5. Select the command in the following table to package the installation package that suits you. The packaged files are in the `/dist_electron` directory. For more information, visit the [electron-builder documentation](https://www.electron.build/cli)

| Command | Description |
| ------------------------------------------ | ------------------------- |
| `yarn electron:build --windows nsis:ia32` | Windows 32-bit |
| `yarn electron:build --windows nsis:arm64` | Windows ARM |
| `yarn electron:build --linux deb:armv7l` | Debian armv7l (Raspberry Pi, etc.) |
| `yarn electron:build --macos dir:arm64` | macOS ARM |

## :computer: Configure the development environment

This project is contributed by [NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi) provides API.

Run this project

```shell
# Install dependencies
yarn install

# Create local environment variables
cp .env.example .env

# Run (web)
yarn serve

# Run (electron)
yarn electron:serve
```

Run NeteaseCloudMusicApi locally, or deploy the API to Vercel (#%EF%B8%8F-deploy to-vercel)

```shell
# Run API (default port 3000)
yarn netease_api:run
```

## ☑️ Todo

To view Todo, please visit [Projects](https://github.com/qier222/YesPlayMusic/projects/1) of this project

Issues and Pull requests are welcome.

## 📜 Open Source License

This project is for personal study and research only. Commercial and illegal use is prohibited.

Open source based on [MIT license](https://opensource.org/licenses/MIT).

## Inspiration

API source code from [Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)

- [Apple Music](https://music.apple.com)
- [YouTube Music](https://music.youtube.com)
- [Spotify](https://www.spotify.com)
- [NetEase Cloud Music](https://music.163.com)

## 🖼️ Screenshots
![lyrics][lyrics-screenshot]
![library-dark][library-dark-screenshot]
![album][album-screenshot]
![home-2][home-2-screenshot]
![artist][artist-screenshot]
![search][search-screenshot]
![home][home-screenshot]
![explore][explore-screenshot]

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[album-screenshot]: images/album.png
[artist-screenshot]: images/artist.png
[explore-screenshot]: images/explore.png
[home-screenshot]: images/home.png
[home-2-screenshot]: images/home-2.png
[lyrics-screenshot]: images/lyrics.png
[library-screenshot]: images/library.png
[library-dark-screenshot]: images/library-dark.png
[search-screenshot]: images/search.png
