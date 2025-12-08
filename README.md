#NPM example for the purpose of showing secure dependency version locking. 

1) Broad dependencies in package.js only locked to Major versions using ^
>  "dependencies": {  
>    "express": "^4",  
>    "cors": "^2",  
>    "dayjs": "^1"  
>  }
3) Run `npm install` to create package-lock.json with specific version locks and SHA package validation (defeats supply chain hacks to current versions)
4) In CI/CD pipelines run `npm ci` rather than `npm install` to do a clean install from the lockfile
