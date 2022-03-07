---
typora-copy-images-to: imagens
---

# how_to_update_docker_image



Passo 1: Rodar a Imagem que deseja alterar

```bash
docker run -u root -it --rm strink/tornado:batch-inference-jupyter
```

Passo 2: instalar pytorch(Stable (1.9.0)/Linux/Pip/Python/CUDA 10.2)

```bash
pip3 install torch torchvision torchaudio
```

![image-20210822132441305](https://github.com/niltonmalves/how_to_update_docker_image/blob/main/imagens/image-20210822132441305.png?raw=true)

Passo 3: instalar detectron para CUDA 10.2 e pytorch(Stable (1.9.0)

Link onde foi retirado o camando abaixo foi [aqui](https://detectron2.readthedocs.io/en/latest/tutorials/install.html).

```bash
python -m pip install detectron2 -f \
  https://dl.fbaipublicfiles.com/detectron2/wheels/cu102/torch1.9/index.html
```

![image-20210822132845552](https://github.com/niltonmalves/how_to_update_docker_image/blob/main/imagens/image-20210822132845552.png?raw=true)



Passo 4: Salvar as alterações feita na imagem. O Ideal é deixar a imagem rodando e abrir outra conexão e fazer o comit da imagem ativa, que foi alterada.

** Atenção verificar a necessidade de fazer um stop container  antes de comitar, conforme informado nesse [link](https://stack.desenvolvedor.expert/appendix/docker/criandoimagem.html) **

Para verificar o id da imagem, usar:

```bash
docker ps 
```

Identificar o ID da imagem e fazer comit com um nome novo para imagem.

```bash
docker commit d39cd8c1e63c strink/tornado:jupyter
```

Pronto a imagem está alterada.

Falta enviar para o docker hub - Verificar no google como faz :)



------

Uma boa prática de alteração de imagem é através a criação do Docker file, para as alterações acima seria:



```dockerfile
# syntax=docker/dockerfile:1
FROM strink/tornado:batch-inference-jupyter
CMD python pip3 install torch torchvision torchaudio

CMD python -m pip install detectron2 -f \
  https://dl.fbaipublicfiles.com/detectron2/wheels/cu102/torch1.9/index.html


```

