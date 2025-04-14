```bash
lsof -i :<port_number>
```

or

```bash
sudo kill -9 $(lsof -t -i :5000)
```

or

```bash
PORT=8080
sudo kill -9 $(lsof -t -i :$(PORT))
```