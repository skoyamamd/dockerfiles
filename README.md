
### Run interactive

```docker container run -it ubuntu:20.04 /bin/bash```

### Bind directory

```docker container run -it --mount type='bind',source=/Users,target/BoundUsers ubuntu:20.04 /bin/bash```
```docker container run -it --v /Users:/BoundUsers ubuntu:20.04 /bin/bash```

### Build image

```docker image build -t xxxx/sample:latest .```

### Push image

```docker push xxxx/sample:latest```

### Set envirionment variables

```ENV PERL_MM_USE_DEFAULT=1```
```ENV DEVIAN_FRONTEND=noninteractive```

### Set path

```ENV PATH="/opt/local/:${PATH}"```


