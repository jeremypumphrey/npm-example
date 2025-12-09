# NPM example with version locking + SHA–based integrity
## To reduce JavaScript/npm project supply-chain risk (e.g., npm registry compromises like the recent Shai-Hulud incident)

Install requirements:  
`brew install npm-check-updates` easiest for mac 

1) Use Broad dependencies in `package.json` only locked to Major versions using `^`. Human editable
>  "dependencies": {  
>    "express": "^4",  
>    "cors": "^2",  
>    "dayjs": "^1"  
>  }  

2) Run `ncu --cooldown 5 -u` to automatically update dependencies to latest version as long as they are 5 days old
  
3) Run `npm install` to create `package-lock.json` with specific version locks and SHA package validation. Never edit manually.  
>    "node_modules/dayjs": {  
>      "version": "1.11.19",  
>      "resolved": "https://registry.npmjs.org/dayjs/-/dayjs-1.11.19.tgz",  
>      "integrity": "sha512-t5EcLVS6QPBNqM2z8fakk/NKel+Xzshgt8FFKAn+qwlD1pzZWxh0nVCrvFK7ZDb6XucZeF9z8C7CBWTRIVApAw==",  
>      "license": "MIT"  
>    },  

4) Run `npm audit fix` to ensure you aren't locked to known vulnerable packages  

5) Commit the `package-lock.json` file
 
6) In CI/CD pipelines run `npm ci` rather than `npm install` to do a clean install using only versions (SHA based) and depenedencies from the lockfile
