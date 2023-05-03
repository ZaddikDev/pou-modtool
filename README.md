# Pou mod tool
A mod tool for Pou that builds the mods for the pou modloader.

![unnamed](https://user-images.githubusercontent.com/63800482/235944667-b1d99c61-a993-4e24-bca9-631756017905.png)

> NOTE: While the sound modding is being worked on, mod building is done by simply compressing the files as .zip


## Creating a mod
To create a mod, you will need several files and folders to make it work.

#### Create a mod.json
To make the mod work, you will need to create the main file (`mod.json`), where the info such as the name, description and author are.

Once you create the file, write this to it:

```json
{
    "name": "<Put your mod name here>",
    "description": "<Put your mod description here>",
    "author": "<Put the mod author name here>"
}
```

Replace all the text between `<>` with yours.

#### Creating a manifest.json
For the next steps, you will need this plain `mainfest.json`

Create a file with that name and open it with your preferred text editor. After that, paste this text:

```json
{
    "images": {},
    "sounds": {},
    "items": {},
    "lang": {}
}
```

This file will list all the modified files and their respective path.

#### Modifying an image
To modify an image or text, you will have to decompile Pou's APK. You can download it from this repository's [release page](https://github.com/ZaddikDev/pou-modtool/releases/) and you can decompile it using [APK Tool](https://ibotpeaches.github.io/Apktool/).

Then, you have to open the `assets` folder and then the `images` subfolder. Now search for any image and get its path.

> Note: The path separator needs to be `/`, NOT `\`.

After doing that, crop the file path until you don't have `assets/images`.

Example: `C:/Users/User/Downloads/Pou/assets/images/food/cherries.png` -> `food/cherries.png`

Then you go to your mod folder and create a folder called `assets` and inside it create another folder called `images`. Then create folders and the image that replicate the path you copied.

> Note: Your image will look better if the size of the image is the same as the original one

After you do that, go to your mod root folder and open `manifest.json`.

Add this entry to `images`:
```json
{
    "images": 
    {
        "<put your copied path here>": "<put your new path here>"
    },
    [...]
}
```

Remember replacing the text inside `<>` with your own.

Example:
`"food/cherries.png": "food/hello.png"`

#### Modifying text
To modify an image or text, you will have to decompile Pou's APK. You can download it from this repository's [release page](https://github.com/ZaddikDev/pou-modtool/releases/) and you can decompile it using [APK Tool](https://ibotpeaches.github.io/Apktool/).

Then, you will have to open the `res` folder and then search for `values`. Some of the folders that start with that will have a `-` symbol with 2 letters after. That specifies the language. Open your language folder (if you speak english, open the `values` folder without suffix. Then, you must open the `strings.xml` folder. That contains almost all the text in the game. Every entry is a text in-game. Now, search for your text and copy its ID.

Example: `<string name="coins_to_buy">You need # more coins in order to buy this.</string> -> coins_to_buy`

Then go to your `manifest.json` in your mod folder and modify the `lang` entry adding your entry.

```json
{
    [...],
    "lang": 
    {
        "<put your copied ID>": "<put your new text here>"
    }
}
```

Remember replacing the text inside `<>` with your own.

Example:
`"coins_to_buy": "You need # coins to buy this article."`

#### Building a mod
Go to your mod root folder and zip all the files (If you dow't know how to do that you can use [7-zip](https://www.7-zip.org/))

Change the file extension to .pou and then install it onto your Pou mod loader copy (if you don't have one you can download one at the [releases](https://github.com/ZaddikDev/pou-modtool/releases/) page).
