# meteor-package

The Meteor framework has its own packaging system apart from npm that uses packages from [atmospherejs.com](https://atmospherejs.com/). 
This package exists to make integrating npm packages with Atmosphere packages easy. 

## Define Meteor Dependencies

Inside your npm package or non-Meteor code, you can rely on a Meteor package by simply getting it in the proper environment (client or server) like this:

```javascript
import { getMeteorClientPackage,  getMeteorServerPackage } from 'meteor-package';

// rely on a Meteor package on the client
const SimpleSchema = getMeteorClientPackage('aldeed:simlpe-schema');

// rely on a Meteor package on the server
const cluster = getMeteorServerPackage('meteorhacks:cluster');
```

If the package is missing in the specified environment, an error will be thrown with instructions on how to meet the dependency requirement like this:

```
$: ==> Meteor Package missing: 'aldeed:simple-schema' on client environment.
       Please run 'meteor add aldeed:simple-schema' to satisfy the Meteor 
       package dependency.
```