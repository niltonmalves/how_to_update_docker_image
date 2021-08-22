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

```bash
python -m pip install detectron2 -f \
  https://dl.fbaipublicfiles.com/detectron2/wheels/cu102/torch1.9/index.html
```

![image-20210822132845552](C:\Users\alves\Documents\GitHub\how_to_update_docker_image\imagens\image-20210822132845552.png)