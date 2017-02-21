### Note of NG2—The difference between AOT and JIT
I made some note by my understood from reading the cookbook of NG2 today. 

Here is the note below:

AOT: Ahead of time
For compiling code before any browser load it. Used in Production.

Related:
1. Rollup: The utility that do tree shaking. It only cares modules that have Import and Export statements.
2. ngc: A compiler that provided in the @angular/compiler-cli instead of the Typescript compiler. It has better performance than Typescript compiler for AOT mode in Angular2 application.
3. source-map-explorer: Analyse the source map generated with the bundle and draws a map of all dependencies.

Advantage:
1. Could reduce the HTTP requests of those resources which are individual dependencies.
2. Could do tree shaking to reduce unused portions of both source and library code.
3. Could improve the speed of loading and executing when first load the application with JIT.
4. Could uglify and mangle the final code.
5. It only produces one bundle script.

Disadvantage:
1. Not be friendly with dev mode, it will be slower when the application code larger. And every time we modified the code, it has to be compiled entirely again. It will take a several seconds or more.

JIT: Just in time
For compiling the app in browser runtime when it loads. Used in Development.

Related:
1. SystemJS: It’s a ES module loader, and it could load any module format.

Advantage:
1. It is faster than compile everything in AOT mode so that it is better for the stage development.

Disadvantage:
1. It relies on a browser runtime to compile everything after the source code loaded. That will delay the time could start to use by users.
2. It needs the angular compiler in browser, and the compiler is large and nearly equals to half size of the whole application code.
3. It uses SystemJS to load multiple sources such as templates, css and JS files. It might slower than only one bundle file being loaded.

By the way, it’s the first time I use Keep today.
