# base image
ARG BASE_IMAGE
FROM ${BASE_IMAGE}

# 作業ディレクトリの設定
WORKDIR /root/mp-slave

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y curl

# MultiPaperのdl
ARG MULTIPAPER_SLAVE_URL
RUN curl -o multipaper-master.jar ${MULTIPAPER_SLAVE_URL}

# ポートの公開
EXPOSE 25565

# 起動時に鯖実行
CMD ["java", "-Xmx512M", "-Xms128M", "-jar", "multipaper-master.jar", "25565"]