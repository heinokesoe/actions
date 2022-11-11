### Collection of Github Actions for personal uses.

<details>
<summary>Cloudflare Pages</summary>

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
</details>

<details>
<summary>Hugo</summary>

#### Setup Hugo

#### Usage

```yaml
steps:
  - name: Setup Hugo
    uses: heinokesoe/actions@hugo
    with:
      parameter: --minify -b "https://example.com/"       # This is optional
```
</details>

<details>
<summary>LXD</summary>

#### Setup LXD

#### Usage

```yaml
steps:
  - name: Setup LXD
    uses: heinokesoe/actions@lxd
  - run: lxc launch ubuntu:focal build-server
```
</details>

<details>
<summary>Rclone</summary>

#### Setup Rclone

#### Usage

To use `rclone`, run this action before `rclone`.

Encode the rclone.conf file in base64 using this command `base64 -w 0 rclone.conf` and paste it to `RCLONE_CONFIG` secret.

```yaml
steps:
  - name: Setup Rclone
    uses: heinokesoe/actions@rclone
    with:
      rclone_config: ${{ secrets.RCLONE_CONFIG }}
  - run: rclone copy source:sourcepath dest:destpath
```

For bare remote with exposed colon, use single quotes to prevent the YAML parser from the ambiguity of colon.

```yaml
steps:
  - name: Setup Rclone
    uses: heinokesoe/actions@rclone
    with:
      rclone_config: ${{ secrets.RCLONE_CONFIG }}
  - run: 'rclone copy source: dest:'
```
</details>

<details>
<summary>Tool Cache</summary>

#### Setup Tool Cache

#### Usage

1. Create a folder with the name of the program you want to install inside `${{ runner.temp }}`.
2. Extract all of the files required by the program to that folder inside `${{ runner.temp }}` you have created.
3. Run this action with the name of the folder inside `${{ runner.temp }}` you used to extract all the files needed for the program.

```yaml
steps:
  - name: Install the Hello World binary using tool-cache
    uses: heinokesoe/actions@tool-cache
    with:
      folder_name: hello-world-program
```
</details>
