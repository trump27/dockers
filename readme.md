# Tips

## ip確認
```
docker-machine ip [container]
```

## コンテナ、イメージ削除

```
docker rm `docker ps -a -q`
docker rmi `docker images -a -q`

docker rmi $(docker images -a | awk '/^<none>/ { print $3 }')
```

## Storageパス変更

defaultのdocker-machineのパスを指定し再作成。
```bash
docker-machine -s "D:\Docker Toolbox\machine" create --driver virtualbox default
```
* デフォルトのパスを変更したときは、環境変数``MACHINE_STORAGE_PATH``にそのパスを指定すること。

## 共有フォルダの追加

初期でc/Userが共有フォルダとなっている。しかし新たにVirtualboxの共有フォルダ作成UIで追加しても、VM側ではフォルダ名しか認識しない。
手動で作成する。
* defaultのVMを停止する
* (初回1回のみ)コマンドプロンプトで共有設定を追加する。ここでは``d``という名前で``d:\``を共有設定している。
```
VBoxManage.exe sharedfolder add default -name d -hostpath d:\
```
* （virtualbox起動時に毎回実施）次にdefaultのVMを起動し、sshで設定する。
```
docker-machine.exe ssh default 'sudo mkdir /d'
docker-machine.exe ssh default 'sudo mount -t vboxsf -o uid=0,gid=0 d /d'
```
