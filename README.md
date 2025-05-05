# 2025cloud

* Author: NTU CSIE r13922044 楊子慶
* Info: Cloud Native 2025 Spring Hw4

## Links

* Github: [https://github.com/Shiritai/2025cloud](https://github.com/Shiritai/2025cloud)
* Docker hub: [https://hub.docker.com/repository/docker/eroiko/2025cloud](https://hub.docker.com/repository/docker/eroiko/2025cloud)

## Build

```bash
docker build . -t cloud-native-hw4
```

## Run

```bash
docker run cloud-native-hw4
```

## 自動化

### 何時產生 Image

當 Git push 至 Github 時，會自動觸發 Github Action，其會產生兩個 docker image。

### 產生 Image 時 Tag 選擇邏輯

* `latest`: 基於最新一次 push 所產生的 Image，讓使用者可以取得所有分支中最新的 Image
* `<BRANCH_NAME>`: 基於 push 的分支所產生的 Image，讓使用者可以取用不同分支的 Image