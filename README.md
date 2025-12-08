#NPM example for the purpose of showing secure dependency version locking. 

1) Broad dependencies in package.js only locked to Major versions using ^
>  "dependencies": {  
>    "express": **"^4",  
>    "cors": **"^2",  
>    "dayjs": **"^1"  
>  }  
3) Run `npm install` to create package-lock.json with specific version locks and SHA package validation (defeats supply chain hacks to current versions) 
>    "node_modules/dayjs": {
>      **"version": "1.11.19",
>      "resolved": "https://registry.npmjs.org/dayjs/-/dayjs-1.11.19.tgz",
>      **"integrity": "sha512-t5EcLVS6QPBNqM2z8fakk/NKel+Xzshgt8FFKAn+qwlD1pzZWxh0nVCrvFK7ZDb6XucZeF9z8C7CBWTRIVApAw==",
>      "license": "MIT"
>    },  

4) In CI/CD pipelines run `npm ci` rather than `npm install` to do a clean install from the lockfile
