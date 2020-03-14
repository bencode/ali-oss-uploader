# ali-oss-upload-cli


## Usage

### 1. Install package

```shell
npm install --save ali-oss-upload-cli
```

or

```shell
yarn add --dev ali-oss-upload-cli
```

### 2. Add an config file `oss.secret.json` under your project's directory.

```json
{
  "region": "oss-cn-shanghai",
  "bucket": "demo-static",
  "accessKeyId": "xxxxxx",
  "accessKeySecret": "xxxxxx"
}
```

**You should add this secret file to `.gitignore` file for preventing commit.**

[Optional] the config file can also be a js module then you can read `id` and `secret` from process env.

```js
module.exports = {
  region: 'oss-cn-qingdao',
  bucket: 'qgt-paper',
  accessKeyId: process.env.TEST_OSS_ID,
  accessKeySecret: process.env.TEST_OSS_SECRET,
};
```


### 3. Run upload command

```shell
# upload dist dir to remote `/collab-static`
oss-upload dist -o /collab-static -c config/oss.secret.json

# upload to bucket root dir
oss-upload priv/static -o / -c config/oss.secret.json

# config can be a node module
oss-uplaod priv/static -o / -c config/oss.config.js

# omit `-c` if config file is in the default location: $project/oss.config.js
oss-upload dist -o '/'

# clear remote directory before uploading
oss-upload dist -o '/' -C
```

### 4. show help

```shell
oss-upload -h

Usage: oss-upload [options] <dir>

  Options:

    -V, --version        output the version number
    -o, --output <dir>   remote directory
    -C, --clear          clear remote directory before uploading
    -c, --config <file>  oss config file
    -h, --help           output usage information
```
