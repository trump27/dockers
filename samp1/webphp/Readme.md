
```bash
# sampleイメージとしてビルド
docker build -t samplei .

# コンテナ実行 （バックグラウンドモード）
docker run -d -p 80:80 --name samplec samplei

# 実行中コンテナでshell
docker exec -it samplec bash
```
