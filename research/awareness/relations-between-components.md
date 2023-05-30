# Relations Between Components

## Service Agents

The usage of service agents to monitor specific features can be implemented as such:

```ru
module ServiceA {
    func someFn(someArg) {
        NetworkService.HttpReq().get();
    }
}
```

## Specifying SLOs

More than manual specification, inheritance can be enabled for components to know which goal they're contributing to.

```
module Service A:
    FastHTTPSpeed
    ErrorRecoverability {
        func someFn() {
            http.get()
        }
    }
```