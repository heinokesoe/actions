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
