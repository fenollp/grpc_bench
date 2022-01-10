FROM docker.io/library/pypy:3@sha256:80250e1b26bea4e3c8e2a99b0e9a46798959a9cea59bbd9d35eded710541c224

WORKDIR /app
RUN python -m pip install --upgrade pip
RUN python -m pip install asyncio grpcio==1.26.0 grpcio-tools==1.26.0
COPY proto proto
RUN python -m grpc_tools.protoc -I/app/proto/helloworld --python_out=. --grpc_python_out=. helloworld.proto
COPY python_async_pypy_grpc_bench .

ENTRYPOINT [ "pypy", "/app/server.py" ]
