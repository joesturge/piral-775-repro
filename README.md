# Reproduction for Issue 775 Piral

## My Env

- Node: v22.14.0
- NPM: v10.9.2
- OS: Windows 11 WSL2

## Steps to reproduce


```
npm i
npm start
```

Open up the latest version of Firefox and navigate to http://localhost:1234

Right click open up web console log and observere the following:

```
Uncaught Error: Permission denied to access property "toJSON"
    derez decycle.js:5
    derez decycle.js:40
    derez decycle.js:40
    derez decycle.js:40
    derez decycle.js:40
    derez decycle.js:40
    decycle decycle.js:54
    dispatchEvent debug.js:317
    emit piral-base-full.mjs:1733
    Mediator Mediator.js:14
    React 8
    workLoop scheduler.development.js:266
    flushWork scheduler.development.js:239
    performWorkUntilDeadline scheduler.development.js:533
    requireScheduler_development scheduler.development.js:571
    requireScheduler_development scheduler.development.js:633
    requireScheduler_development scheduler.development.js:634
    requireScheduler index.js:6
    React 4
    <anonymous> index.BcxpbhZ2.js:58490
decycle.js:5:24
```

## Additional Notes

At first I could not get it to happen then I remembered that you had to add the importmaps to package.json as per: https://docs.piral.io/plugins/piral-ng/. One I added 

```
{
  "importmap": {
    "imports": {
      "@angular/common": "",
      "@angular/compiler": "",
      "@angular/core": "",
      "@angular/platform-browser": "",
      "@angular/platform-browser-dynamic": "",
      "piral-ng-common": "",
      "rxjs": "",
      "zone.js": ""
    }
  }
}
```

To the package.json then the error occured
