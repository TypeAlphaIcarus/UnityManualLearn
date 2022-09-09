# Unity Manual 2021

# 八、图形

## 1、渲染管线

### 1.1、渲染管线介绍

渲染管线获取场景中的一系列内容并执行一系列的操作，然后再屏幕上显示它们，这些操作可以概括为：

剔除(Culling)、渲染(Rendering)、后处理(Post-processing)

不同的渲染管线有不同的性能和表现特性，也分别适用于不同的游戏、应用和平台

在项目中切换渲染管线非常困难，因为不同的渲染管线使用的不同的着色器(shader)输出，而且可能有不同的特征，了解不同的渲染管线非常重要，这样就可以在项目开发的初期尽早做出决策

Unity提供了三种渲染管线

内置渲染管线(Built-in RP)：Unity默认的渲染管线，是一个通用的渲染管线，在自定义方面存在限制

通用渲染管线(Universal RP)：一种可以快速自定义的可编写渲染管线，同时支持各个平台

高清晰度渲染管线(High Definition RP)：可编写的渲染管线，可以在高端平台创建尖端、高保真的图形



### 1.2、渲染管线对比

- [Platform Support](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#platform-support)
- [Lighting](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#lighting)
- [Color](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#color)
- [Camera](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#camera)
- [Shaders](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#shaders)
- [World building](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#world-building)
- [Visual effects](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#visual-effects)
- [2D and UI](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#2d-and-ui)
- [XR](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#xr)
- [Scripting](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#scripting)
- [Optimizations](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#optimizations)
- [Debug](https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#debug)

https://docs.unity3d.com/Manual/render-pipelines-feature-comparison.html#shaders



### 1.3、获取、设置和配置渲染管线

概述

渲染时，Unity可以使用内置的渲染管线或者基于可编写的渲染管线，如URP和HDRP

为了规定Unity使用哪个可编写渲染管线，可以使用渲染管线资产(Assets)，一个渲染管线资产告诉Unity去使用哪个可编写渲染管线，和如何设置渲染管线，如果不配置渲染管线资产，那么Untiy就会使用内置渲染管线

在使用同一渲染管线时，可以定义多个渲染管线资产，来进行不同的配置，这样就能匹配不同水平的硬件

一旦改变激活的渲染管线之后，unity就会使用最新激活的渲染管线去渲染所有内容，包括游戏视图、场景视图以及观察面包中材质的预览视图

在设置中的Graphic选项和Quality选项都可以设置激活哪个渲染管线资产，在图形设置中，可以配置Unity默认使用的渲染管线。在“质量设置”中，可以覆盖给定质量级别的渲染管线。

除此以外，还可以调用API来设置渲染管线

```C#
public RenderPipelineAsset renderPipelineAsset;
void Start()
{
    GraphicsSettings.defaultRenderPipeline = renderPipelineAsset;
}

```

