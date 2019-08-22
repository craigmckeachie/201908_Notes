# Angular Course Notes

August 2019 | Instructor: Craig McKeachie

- [Angular Demo Manual](https://s3.amazonaws.com/lib.accelebrate.com/201908_NBME/AngularDemosManual.pdf?AWSAccessKeyId=AKIAIDHGUGNJBHZ3Z36A&Expires=1566502611&Signature=%2BQ9Gd2gmqvSyaeNOHVv%2Bdn2eHKs%3D)
- [Challenges](http://lib.accelebrate.com/201908_ATT/challenges.zip)

## Day 1

- [ES (JS) Import Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [ES Compatibility Chart](http://kangax.github.io/compat-table/es6/)
- [Mini.css](https://minicss.org/)
- [npm install vs npm ci](https://stackoverflow.com/questions/52499617/what-is-the-difference-between-npm-install-and-npm-ci)
- [npm ci](https://docs.npmjs.com/cli/ci.html)
- [npm ci announcement](https://blog.npmjs.org/post/171556855892/introducing-npm-ci-for-faster-more-reliable)
- [TypeScript Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
- [Prettier (code formatter)](https://prettier.io/)
- [Prettier Language Support](https://prettier.io/docs/en/index.html)

## Day 2

- [DatePipe](https://angular.io/api/common/DatePipe)
- [Emmet:HTML Completion Cheatsheet](https://docs.emmet.io/cheat-sheet/)
- [Select: Dropdowns](https://angular.io/api/forms/SelectControlValueAccessor)
- [Material Design Dropdowns](https://material.angular.io/components/select/overview)

### Libraries

- [Creating Libraries](https://angular.io/guide/creating-libraries)
- [Workspace & Project File Structure](https://angular.io/guide/file-structure#library-project-files)

## Virtual

- [Link for Remote Attendees](https://attendee.gototraining.com/r/6017775973692715009)
- [Virtual Machine for Labs](https://gist.github.com/craigmckeachie/08c0c2be7ed8fac5a1ba97aa4ea4c4d3)

## UI Frameworks

In general, this page on the Angular documentation lists all the options.
https://angular.io/resources#ui-components

In my opinion the 4 Best UI Component Suites for Angular are:

- Material: https://material.angular.io/ (open source/free)
- Clarity: https://vmware.github.io/clarity/ (open source/free)
- Kendo: https://www.telerik.com/kendo-angular-ui (open source/paid)
- Bootstrap: https://ng-bootstrap.github.io/#/home (open source/free)

# Angular Resources

[Angular Documentation](https://angular.io/docs)

[The Unofficial Angular Documentation](http://ngdoc.io/)

[Angular in Depth](https://blog.angularindepth.com/best-stories-of-2018-on-angular-in-depth-80a1dfa17fd5)

[Nrwl: Enterprise Angular Consulting Blog](https://blog.nrwl.io/)

[Todd Motto Blog](https://toddmotto.com/)

---

# Courseware Errata Version 8.0.3.0

## npm audit vulnerabilities

Within a few weeks of publishing the course there quickly appeared over 100 security vulnerabilities reported in the libraries that Angular and the testing frameworks used in an Angular CLI project. I fixed these in the over 100 branches of the code included with the courseware and 2 weeks later 100+ new vulnerabilities appeared.

All of that to say keeping up with the patching of the npm packages for security vulnerabilities reported from npm audit is a moving target.

That said I will produce regular releases attempting to patch these issues but in between those releases I would use it as a learning opportunity during class.

1. Explain the situation as I have above and let attendees know they will have this same problem in their applications.
2. Run the following command:

```
npm audit
```

3. Scroll through the list of audit issues to show them that they could fix certain issues individually by running the command associated with each.
4. Or they can fix all the issues at once but run a greater chance of the code breaking.
5. Run the following commmands in one of the project-manage directories:

```
git init .
git checkout -b audit-fixes
npm audit fix
```

- the first two commands are creating a local git repo for the code and then branching it so if things don't work after updating the dependencies you can just rollback the changes

6. Run the application

```
ng serve -o
npm run applications
```

7. Verify the app still runs.
8. If it doesn't explain that you would either wait a few weeks before doing the update or use only certain of the updates commands from the `npm audit` that were high severity and didn't break the application.

## Lab 2 End

Since differential builds are enabled by default in the Angular CLI to get the project to display in IE 11 or lower you would need to turn off differential builds by following these steps in Lab 29: Step 19 a & b (be sure to the additional information below).

## Lab 4 & 5

Instead of grouping labs
Lab 4
then
Lab 5,6,7

---

consider doing
Lab 4,5
then
Lab 6,7

## Lab 5 Step 2

The command skipTests should include two hypens before it as shown below.

```
ng g class projects/shared/project --skipTests
```

Alternatively you could run the following command to tell the Angular CLI that you want to create a class that is a model so you want to name the file `project.model.ts` NOT `project.ts`

```
ng g class projects/shared/project  --skipTests --type='model'
```

> --type
>
> Adds a developer-defined type to the filename, in the format "name.type.ts".

## Lab 5: Step 6

The code snippet is correct and uses `MOCK_PROJECTS` as the variable name, however the code block in the book still names the variable `PROJECTS` not `MOCK_PROJECTS`

> Most people will not notice this but someone may point it out

## Lab 18, step 2

? in template is not required

## Lab 29: Step 19 a

### project-manage\tsconfig.json

```diff
{
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "downlevelIteration": true,
    "importHelpers": true,
    "outDir": "./dist/out-tsc",
    "sourceMap": true,
    "declaration": false,
    "module": "esnext",
    "moduleResolution": "node",
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
-    "target": "es2015",
+    "target": "es5",

    ...
  }
}
```

## Lab 29: Step 19 b

### project-manage\browserslist

```diff
# This file is currently used by autoprefixer to adjust CSS to support the below specified browsers
# For additional information regarding the format and rule options, please see:
# https://github.com/browserslist/browserslist#queries
#
# For IE 9-11 support, please remove 'not' from the last line of the file and adjust as needed

> 0.5%
last 2 versions
Firefox ESR
not dead
- not IE 9-11
+ IE 9-11

```

## Unit Testing Lab 3: Step 4

Code snippet doesn't include import for project object which needs to be added.
See below for import path if needed.

```js
import { Project } from '../shared/project.model';
```
