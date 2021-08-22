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