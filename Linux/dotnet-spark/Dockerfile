ARG DOTNET_CORE_VERSION=3.1
FROM 3rdman/dotnet-sdk-linux:$DOTNET_CORE_VERSION

ARG DOTNET_SPARK_VERSION=0.11.0
ENV DOTNET_SPARK_VERSION=$DOTNET_SPARK_VERSION
ENV DOTNET_WORKER_DIR=/dotnet/Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION}

RUN mkdir -p /dotnet/HelloSpark \
    && mkdir -p /dotnet/Debug/netcoreapp${DOTNET_CORE_VERSION} \
    && mkdir /tempdata \
    && chmod 777 /tempdata \
    && wget https://github.com/dotnet/spark/releases/download/v${DOTNET_SPARK_VERSION}/Microsoft.Spark.Worker.netcoreapp${DOTNET_CORE_VERSION}.linux-x64-${DOTNET_SPARK_VERSION}.tar.gz \
    && tar -xvzf Microsoft.Spark.Worker.netcoreapp${DOTNET_CORE_VERSION}.linux-x64-${DOTNET_SPARK_VERSION}.tar.gz \
    && mv Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION} /dotnet/ \
    && cp /dotnet/Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION}/Microsoft.Spark.Worker /dotnet/Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION}/Microsoft.Spark.Worker.exe \
    && chmod 755 /dotnet/Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION}/Microsoft.Spark.Worker \
    && chmod 755 /dotnet/Microsoft.Spark.Worker-${DOTNET_SPARK_VERSION}/Microsoft.Spark.Worker.exe \
    && rm Microsoft.Spark.Worker.netcoreapp${DOTNET_CORE_VERSION}.linux-x64-${DOTNET_SPARK_VERSION}.tar.gz

COPY HelloSpark /dotnet/HelloSpark

RUN cd /dotnet/HelloSpark \
    && dotnet build \
    && cp /dotnet/HelloSpark/bin/Debug/netcoreapp${DOTNET_CORE_VERSION}/microsoft-spark-*.jar /dotnet/Debug/netcoreapp${DOTNET_CORE_VERSION}/


