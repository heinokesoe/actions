#### Build with hugo and publish to cloudflare pages

#### Usage

1. Create the secret for cloudflare api token with CF_API name.
2. Create the secret for cloudflare account id with CF_ID name.

```yaml
steps:
  - name: Build with hugo and publish to cloudflare pages
    uses: heinokesoe/actions@cloudflare-pages
    with:
      apiToken: ${{ secrets.CF_API }}
      accountID: ${{ secrets.CF_ID }}
      projectName: <project name you want to create and publish>
```
