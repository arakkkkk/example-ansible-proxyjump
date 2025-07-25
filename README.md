# example-ansible-proxyjump

## 構成
```mermaid
graph LR
    A[ローカルマシン<br/>Ansible実行サーバー] -->|SSH:2222<br>公開鍵認証| B[踏み台サーバー<br/>192.168.11.10]
    B -->|SSH:2222<br>公開鍵認証| C[対象サーバー<br/>192.168.122.70]
    
    style A fill:#e1f5fe
    style B fill:#fff3e0
    style C fill:#f3e5f5
```

## Usage

### 疎通テスト
```
ansible -i hosts ansible-client -m ping
```

### 実行
```
ansible-playbook -i hosts pb-test_role.yml -vvv
```

## Note
対象サーバーをパスワードで認証する場合、`sshpass`のインストールが必要。

```
sudo apt install -y sshpass
```
