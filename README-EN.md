![](public/brand.png)

<div align="center">

[简体中文](./README.md) / English

Github Stars Repositories Manager, A must-have repository management tool for developers

</div>

## 🎯 Situation

As the first social platform for developers, Github has countless excellent open source projects, which brings great convenience to work and study. When you encounter a project you need or like, just click Star to get it.

Star is easy, but as the number of Starred Repositories grows, it is inevitable that you can’t remember the name of a certain project when you need to use it, and Github only provides a simple search, so finding the target Starred Repository has become a little troublesome.

Therefore, having your own Github Stars Repositories Manager is also a must-have for developers. 💡

## 👀 Discover good projects: Gitstars Ranking (2023-09-09)

<strong>Gitstars Ranking</strong>: Helps you discover the top 100 good projects with the number of Github Stars. It supports various programming language categories and is updated daily.

![](public/example-github-ranking.png)

## 🚀 Quickly find your Star’s warehouse: Your Stars

<strong>Your Stars</strong>: Organize your Stars warehouse and classify it according to Topics and Language to help you quickly find target projects.

![](public/example-your-stars.png)

## 👻 Other features

- <strong>README.md preview</strong>: No need to jump to Github to view README.md, you can view it on Gitstars;
- <strong>Direct link</strong>: Github warehouse, project website;

## 📖 illustrate

### Topics: Warehouse label set

The tag set is defined by the Repository author and is generally keywords related to the Repository, mostly in English.

![](public/example-topics.png)

### Language: The main programming language of the warehouse

Github will statistically analyze the files of the Repository and determine the main programming language of the Repository.

![](public/example-languages.png)

## 🤖 Vercel deployment

[WIKI Vercel deployment](https://github.com/cfour-hi/gitstars/wiki/Vercel-%E9%83%A8%E7%BD%B2)

## 🐳 Docker deployment

1. Create an OAuth App in [GitHub Developer Settings](https://github.com/settings/developers), then set its `Authorization callback URL` to `https://localhost:8080`.
2. Copy the environment template and enter the OAuth App's Client ID and Client Secret:

   ```bash
   cp .env.example .env
   ```

3. Generate and trust a local HTTPS certificate with [mkcert](https://github.com/FiloSottile/mkcert):

   ```bash
   pnpm cert:local
   ```

4. Build and start the service:

   ```bash
   docker compose up -d --build
   ```

The service is available at [https://localhost:8080](https://localhost:8080) by default, and its health endpoint is `https://localhost:8080/healthz`. Certificates are mounted read-only and are not stored in the image. Set `GITSTARS_PORT` in `.env` to use another host port, or `GITSTARS_CERT_DIR` to use another certificate directory. The Client ID is embedded in the frontend during the build, so rebuild after changing it. The Client Secret is injected only at runtime and is not stored in the image.

Stop the service with:

```bash
docker compose down
```
