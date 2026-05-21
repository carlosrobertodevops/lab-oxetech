## AWS

### aws criar bucket

```bash
aws s3api create-bucket --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) --region us-east-1
```

### Copiar arquivo txt

```bash
echo "Hello Cloud" > arquivo.txt && aws s3 cp arquivo.txt s3://s3-oxetech-local-deployment-bucket/dados/arquivo.txt
```

### Copiar arquivo de imagem

```bash
aws s3api put-object \ --bucket s3-oxetech-local-deployment-bucket \ --key image.jpg \ --body image.jpg
```

### Versionamentos

```bash
aws s3api put-bucket-versioning --bucket cloud-lab-504132672503-1779315417 --versioning-configuration Status=Enabled
```

### Link temporário

```bash
aws s3 presign s3://cloud-lab-504132672503-1779317812/dados/arquivo.txt --expires-in 3600
```

### Block publico

```bash
aws s3api put-public-access-block --bucket cloud-lab-504132672503-1779317812 --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"
```

### Verificar o Bloqueio

```bash
aws s3api get-public-access-block --bucket cloud-lab-504132672503-1779317812
```

## LOCASTACK

```bash
tflocal apply
```

### Copiar arquivo txt

```bash
aws s3 cp arquivo.txt s3://s3-oxetech-local-deployment-bucket/dados/arqsuivo.txt
```

### Versionamentos

```bash
aws s3api put-bucket-versioning --bucket s3-oxetech-local-deployment-bucket --versioning-configuration Status=Enabled
```

### Copiar arquivo de Imagem

```bash
aws s3 cp arquivo.png s3://s3-oxetech-local-deployment-bucket/image/arquivo.png
```

### Link temporário

```bash
aws s3 presign 3://s3-oxetech-local-deployment-bucket/dados/arquivo.txt --expires-in 3600
```

### Block publico

```bash
aws s3api put-public-access-block --bucket s3-oxetech-local-deployment-bucket --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"
```

### Verificar o Bloqueio

```bash
aws s3api get-public-access-block --bucket s3-oxetech-local-deployment-bucket
```
