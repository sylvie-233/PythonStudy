# passlib



## 基础介绍

Python 密码哈希库，广泛用于处理密码存储、校验等功能，支持多种哈希算法（如 bcrypt、pbkdf2、argon2 等）

## 核心内容
```yaml
passlib:
    context:
        CryptContext:
    hash:
        argon2:
        bcrypt:
            hash():
            verify():
        pbkdf2_sha256:
        sha512_crypt:
```