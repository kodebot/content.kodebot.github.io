# kodebot learning portal


## Run locally
`hugo run -D`

`-D` includes draft documents as well

run hugo to generate the content -> it is generated into docs folder

create pr to merge the generated content into master branch to publish the changes

## How to create new blog post

`hugo new blog\<year>\<blog-title-in-kebab-case>\index`

Example:
`hugo new blog\2021\what-is-cardano-and-ada\index`

Note: This will ensure each post has its own folder with necessary images, attachments, etc


## How to write consistently
Use `h3` (###) onwards for subtitles 
Always create a folder per post and keep all local files in the folder


## Troubleshooting
1. if you have problem with using variable and want to see what is in it use `{{ .VARIABLE | jsonify}}`. This will print the variable and its value as json on the page