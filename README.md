## Denoising Diffusion Probabilistic Models

This is a pytorch implementation of DDPM. The original paper is here https://arxiv.org/abs/2006.11239 .

If you want to know more about the framwork of DDPM, these two blogs may help you: 

* https://zhuanlan.zhihu.com/p/563661713
* https://lilianweng.github.io/posts/2021-07-11-diffusion-models/#:~:text=Diffusion%20models%20are%20inspired%20by,data%20samples%20from%20the%20noise



## how to use

Almost all the parameters that can be modified are listed in the `config.yml` file. You can modify the relevant parameters as needed, and then run the `train.py` file to start training.

After training, run the `generate.py` file to generate the results. These are the parameters of `generate.py` :

* `-cp` : the path of checkpoint.
* `--device` : device used. `'cuda'` (default) or `'cpu'`.
* `-bs` : how many images to generate at once. Default  `16`.
* `--result_only` : whether to output only the generated results. Default  `False`.
* `--interval` : extract an image every how many steps. Only valid without the `result_only` parameter. Default  `50`.
* `--nrow` : how many images are displayed in a row. Only valid with the `result_only` parameter. Default  `4`.
* `--show` : whether to display the result image. Default  `False`.
* `-sp` : save path of the result image. Default  `None`.
* `--to_grayscale` : convert images to grayscale. Default  `False`.



## Some generated images

* MNIST，[click to download checkpoint](https://drive.google.com/file/d/1gwhczBWOjUtw4Fz_y2PidyKnrUsMSN8t/view?usp=drive_link)

```shell
python generate.py -cp "checkpoint/mnist.pth" -bs 16 --interval 10 --show -sp "data/result/mnist_sampler.png"
```


![](data/result/mnist_sampler.png)

```shell
python generate.py -cp "checkpoint/mnist.pth" -bs 256 --show -sp "data/result/mnist_result.png" --nrow 16 --result_only
```

![](data/result/mnist_result.png)

* CIFAR10, [click to download checkpoint](https://drive.google.com/file/d/1GRVfLSfjGtEPJzxg52k4wj4w2TKk-utO/view?usp=drive_link)

```shell
python generate.py -cp "checkpoint/cifar10.pth" -bs 16 --interval 50 --show -sp "data/result/cifar10_sampler.png"
```

![](data/result/cifar10_sampler.png)

```shell
python generate.py -cp "checkpoint/cifar10.pth" -bs 256 --show -sp "data/result/cifar10_result.png" --nrow 16 --result_only
```

![](data/result/cifar10_result.png)

* celeba_hq , [click to download checkpoint](https://drive.google.com/file/d/1iuqXF2K2ezSFZO7PYO-4lD5XKhyaXT_m/view?usp=drive_link)

```shell
python generate.py -cp "checkpoint/celeba_hq.pth" --interval 30 -bs 16 -sp "data/result/celeba_hq_sampler.png" --show
```

![](./data/result/celeba_hq_sampler.png)

```shell
python generate.py -cp "checkpoint/celeba_hq.pth" -bs 16 -sp "data/result/celeba_hq_result.png" --show --nrow 4 --result_only
```

![](./data/result/celeba_hq_result.png)