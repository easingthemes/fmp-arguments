### Escaping quotes in npm task arguments

1. Using FMP:

```
fmp-arguments $mvn clean install

[INFO] ------------------------------------------------------------------------
[INFO] Building fmp quotes 1.0.0
[INFO] ------------------------------------------------------------------------

[INFO] --- frontend-maven-plugin:1.6:npm (Run Script: run npm task with quotes) @ fmp-quotes ---
[INFO] Running 'npm run fmp -- --myarg "Has Space"' in /fmp-arguments
[INFO]
[INFO] > node ./index "--myarg" "\"Has" "Space\""
[INFO]
[INFO] [ '"Has', 'Space"' ]

[INFO] --- frontend-maven-plugin:1.6:npm (Run Script: run npm task with escaped quotes) @ fmp-quotes ---
[INFO] Running 'npm run fmp -- --myarg \"Has Space\"' in /fmp-arguments
[INFO]
[INFO] > node ./index "--myarg" "\\"Has" "Space\\""
[INFO]
[INFO] [ '\\Has Space\\' ]

[INFO] --- frontend-maven-plugin:1.6:npm (Run Script: run npm task without quotes) @ fmp-quotes ---
[INFO] Running 'npm run fmp -- --myarg Has Space' in /fmp-arguments
[INFO] 
[INFO] > node ./index "--myarg" "Has" "Space"
[INFO] 
[INFO] [ 'Has', 'Space' ]

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```

2. Runing in console:

```
fmp-arguments $npm run fmp -- --myarg "Has Space"
> node ./index "--myarg" "Has Space"
[ 'Has Space' ]

fmp-arguments $npm run fmp -- --myarg \"Has Space\"
> node ./index "--myarg" "\"Has" "Space\""
[ '"Has', 'Space"' ]

fmp-arguments $npm run fmp -- --myarg Has Space
> node ./index "--myarg" "Has" "Space"
[ 'Has', 'Space' ]
```

