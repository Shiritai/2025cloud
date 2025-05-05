# 2025cloud

* Author: NTU CSIE r13922044 楊子慶
* Info: Cloud Native 2025 Spring Hw4

## Links

* Github: [https://github.com/Shiritai/2025cloud](https://github.com/Shiritai/2025cloud)
* Docker hub: [https://hub.docker.com/repository/docker/eroiko/2025cloud](https://hub.docker.com/repository/docker/eroiko/2025cloud)

## Repo 創建過程

1. 至 Docker hub 建立 Repo (eroiko/2025cloud)
2. 申請並記錄 PAT
3. 至 Github 建立 Repo (Shiritai/2025cloud)
4. 在本地端於 `main` 分支實作 `Dockerfile`、`ci.yaml` (後者設定為基於 push 觸發)，並推送至 Github，確認
   1. Github Action 正確運行
   2. Docker hub 中新增兩個 tag 的 image
5. 於 Github 開啟 issue，註明 build image 的方法
6. 在本地端建立新分支 `feat/bad-dockerfile`，修改 `Dockerfile` 使其在本地進行 `docker build` 時失敗
7. 將 `feat/bad-dockerfile` push 至 Github 後，確認 Github Action 運行失敗
8. 提出基於 `feat/bad-dockerfile` 的 PR，說明細節

## Build

```bash
docker build . -t cloud-native-hw4
```

## Run

* Run after local build

    ```bash
    docker run cloud-native-hw4
    ```

* Run using docker hub image
  * `latest`

    ```bash
    docker run eroiko/2025cloud:latest
    ```

  * Based on certain branch

    ```bash
    docker run eroiko/2025cloud:<branch_name>
    ```

## 自動化

### 何時產生 Image

當 Git push 至 Github 時，會自動觸發 Github Action，其會產生兩個 docker image。

### 產生 Image 時 Tag 選擇邏輯

* `latest`: 基於最新一次 push 所產生的 Image，讓使用者可以取得所有分支中最新的 Image
* `<BRANCH_NAME>`: 基於 push 的分支所產生的 Image，讓使用者可以取用不同分支的 Image

### Github Action Links

自動執行 docker build 和 push

[https://github.com/Shiritai/2025cloud/actions/runs/14829149884/job/41627003008](https://github.com/Shiritai/2025cloud/actions/runs/14829149884/job/41627003008)
