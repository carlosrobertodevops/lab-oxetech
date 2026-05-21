# OXETECH - LAB

## Comandos usando em sala de aula

## AWS

```bash
### aws criar bucket
aws s3api create-bucket --bucket cloud-lab-$(aws sts get-caller-identity --query Account --output text)-$(date +%s) --region us-east-1

### Copiar arquivo txt
echo "Hello Cloud" > arquivo.txt && aws s3 cp arquivo.txt s3://s3-oxetech-local-deployment-bucket/dados/arquivo.txt

### Copiar arquivo de imagem
aws s3api put-object \ --bucket s3-oxetech-local-deployment-bucket \ --key image.jpg \ --body image.jpg

### Versionamentos
aws s3api put-bucket-versioning --bucket cloud-lab-504132672503-1779315417 --versioning-configuration Status=Enabled

### Link temporário
aws s3 presign s3://cloud-lab-504132672503-1779317812/dados/arquivo.txt --expires-in 3600

### Block publico
aws s3api put-public-access-block --bucket cloud-lab-504132672503-1779317812 --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"

### Verificar o Bloqueio
aws s3api get-public-access-block --bucket cloud-lab-504132672503-1779317812

```

## LOCASTACK

```bash
export NODE_ENV=development
export STAGE=local
export SERVICE_NAME=serverless-elb

# Aws local
export AWS_ACCESS_KEY_ID=test
export AWS_SECRET_ACCESS_KEY=test
export AWS_DEFAULT_REGION=us-east-1

# LocalStack
export LOCALSTACK_HOST=http://localhost
export EDGE_PORT=4566
export AWS_ENDPOINT_URL=http://localhost:4566
export LOCALSTACK_HOSTNAME=localhost
export LOCALSTACK_AUTH_TOKEN="ls-" ## seu TOKEN

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
