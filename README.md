This is a repro of TS6305 errors that arise from TSPR because `--build` does not yet work.

```
$ yarn run tsgo
index.ts:1:21 - error TS6305: Output file '/home/tsgo/tsgo-ts6305/lib/dist/foo.d.ts' has not been built from source file '/home/tsgo/tsgo-ts6305/lib/foo.ts'.

1 import { FOO } from "./lib/foo";
                      ~~~~~~~~~~~

Found 1 error in index.ts:1

error Command failed with exit code 2.
```

If you first run `yarn run tsc --build`, it works:
```
$ yarn run tsc --build
Done in 0.78s.
$ yarn run tsgo
Done in 0.17s.
```

Then to break it again if you clean the build:
```
$ yarn run tsc --build --clean
Done in 0.13s.

$ yarn run tsgo --build
index.ts:1:21 - error TS6305: Output file '/home/tsgo/tsgo-ts6305/lib/dist/foo.d.ts' has not been built from source file '/home/tsgo/tsgo-ts6305/lib/foo.ts'.

1 import { FOO } from "./lib/foo";
                      ~~~~~~~~~~~

Found 1 error in index.ts:1

error Command failed with exit code 2.
```