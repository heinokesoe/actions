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
