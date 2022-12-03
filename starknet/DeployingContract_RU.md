# Официальные ссылки
### [Форма](https://forms.reform.app/starkware/SN-Alpha-Contract-Deployment/l894lu)
### [Оригинал](https://eda.hashnode.dev/developers-guide-to-starknet-and-cairo#heading-create-andamp-deploy-a-smart-contract-withprotostar)

# Создание и деплой смарт-контракта

```
curl -L https://raw.githubusercontent.com/software-mansion/protostar/master/install.sh | bash
```

### Проверяем логи
```
protostar -v
```

### Запускаем компиляцию проекта
```
protostar init
```

### Разворачиваем контракт
```
protostar deploy ./build/main.json --network alpha-goerli
```
