---
description: 깃허브 페이지를 긁어왔음
---

# AMAGI: Active Bleeding Detection

**My github page**: https://sghong977.github.io/bleeding/

## Amplifying Action-context Greater: Image segmentation-guided Active Bleeding Localization in intraoperative gastrectomy

#### Proposed Active Bleeding Framework <a href="#proposed-active-bleeding-framework" id="proposed-active-bleeding-framework"></a>

&#x20;

<figure><img src="https://sghong977.github.io/bleeding/figs/overall.png" alt=""><figcaption></figcaption></figure>

The schematic diagram of active bleeding framework using our proposed model AMAGI.

&#x20;

<figure><img src="https://sghong977.github.io/bleeding/figs/fusion_archi.png" alt=""><figcaption></figcaption></figure>

Proposed fusion-based active bleeding recognition model AMAGI.

#### GradCAM Visualization <a href="#gradcam-visualization" id="gradcam-visualization"></a>

Example gifs

| Data Type | frames                                                                 | Fast Pathway (SlowFast)                                                            | Fast Pathway (AMAGI)                                                                | Fusion Layer (AMAGI)                                                                     |
| --------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Ex1       | ![](https://sghong977.github.io/bleeding/figs/82400\_82408\_conv3.gif) | ![](https://sghong977.github.io/bleeding/figs/sf50\_82400\_82408\_conv3\_gcam.gif) | ![](https://sghong977.github.io/bleeding/figs/amagi\_82400\_82408\_conv3\_gcam.gif) | ![](https://sghong977.github.io/bleeding/figs/amagi\_82400\_82408\_map\_fast2\_gcam.gif) |
| Ex2       | ![](https://sghong977.github.io/bleeding/figs/58160\_58168\_conv3.gif) | ![](https://sghong977.github.io/bleeding/figs/sf50\_58160\_58168\_conv3\_gcam.gif) | ![](https://sghong977.github.io/bleeding/figs/amagi\_58160\_58168\_conv3\_gcam.gif) | ![](https://sghong977.github.io/bleeding/figs/amagi\_58160\_58168\_map\_fast2\_gcam.gif) |

### Surgical Analysis Index <a href="#surgical-analysis-index" id="surgical-analysis-index"></a>

Comparisons of SlowFast and AMAGI on blood count and duration for each 30 test cases.

#### Split 1 <a href="#split-1" id="split-1"></a>

![](https://sghong977.github.io/bleeding/figs/split1.png)

#### Split2 <a href="#split2" id="split2"></a>

![](https://sghong977.github.io/bleeding/figs/split2.png)

#### Split 3 <a href="#split-3" id="split-3"></a>

![](https://sghong977.github.io/bleeding/figs/split3.png)

### Code with pretrained model <a href="#code-with-pretrained-model" id="code-with-pretrained-model"></a>

Here is our [modified version of mmaction2](https://github.com/sghong977/Surgical-Bleeding-AMAGI.git) for active bleeding framework.

1.  Modified implementation of fusion architecture is in

    ```
    ./mmaction/models/{segmentors|heads|backbones}
    ```
2.  train and inference scripts are in

    ```
    ./my_tools/{amagi_train.sh|amagi_inf.sh} 
    ```
3. Pretrained semantic segmentation model and fusion model AMAGI are publicly available in our google drive [here](https://drive.google.com/drive/folders/1dGLRZIEo-kiZZrtXV4XdfdCuEYdsysGb?usp=sharing).
