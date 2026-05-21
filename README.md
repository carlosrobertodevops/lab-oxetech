# OXETECH - LAB

## Comandos usando em sala de aula

## AWS

```bash
### aws criar bucket
aws s3api create-bucket --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) --region us-east-1

### Copiar arquivo txt
echo "Hello Cloud" > arquivo.txt && aws s3 cp arquivo.txt s3://s3-oxetech-local-deployment-bucket/dados/arquivo.txt

### Copiar arquivo de imagem
aws s3api put-object \ --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) \ --key image.jpg \ --body image.jpg

### Versionamentos
aws s3api put-bucket-versioning --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) --versioning-configuration Status=Enabled

### Link temporário
aws s3 presign s3://cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s)/dados/arquivo.txt --expires-in 3600

### Block publico
aws s3api put-public-access-block --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

### Verificar o Bloqueio
aws s3api get-public-access-block --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s)

```

## LOCASTACK

```bash
export GATEWAY_LISTEN="0.0.0.0:4566"
export LOCALSTACK_HOST="localhost.localstack.cloud:4566"
```

```bash
## subir o localstack
localstack start -d

## subir o s3 com terraform
tflocal plan

## subir o s3 com terraform
tflocal apply

### Copiar arquivo txt
aws s3 cp arquivo.txt s3://s3-oxetech-local-deployment-bucket/dados/arqsuivo.txt

### Versionamentos
aws s3api put-bucket-versioning --bucket s3-oxetech-local-deployment-bucket --versioning-configuration Status=Enabled

### Copiar arquivo de Imagem
aws s3 cp arquivo.png s3://s3-oxetech-local-deployment-bucket/image/arquivo.png

### Link temporário
aws s3 presign 3://s3-oxetech-local-deployment-bucket/dados/arquivo.txt --expires-in 3600

### Block publico
aws s3api put-public-access-block --bucket s3-oxetech-local-deployment-bucket --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

### Verificar o Bloqueio
aws s3api get-public-access-block --bucket s3-oxetech-local-deployment-bucket

```
