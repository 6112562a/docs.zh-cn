---
title: 教程：重新定型 TensorFlow 图像分类器 - 迁移学习
description: 了解如何使用迁移学习和 ML.NET 重新定型图像分类器 TensorFlow 模型。 已定型原始模型，可以对单个图像进行分类。 重新定型后，新模型将图像组织成较大类别。
ms.date: 07/09/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: e069abe44b77b1dc31b78ecec1971ccc73f2e012
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054080"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="d2098-105">教程：使用迁移学习和 ML.NET 重新定型 TensorFlow 图像分类器</span><span class="sxs-lookup"><span data-stu-id="d2098-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="d2098-106">了解如何使用迁移学习和 ML.NET 重新定型图像分类器 TensorFlow 模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="d2098-107">已定型原始模型，可以对单个图像进行分类。</span><span class="sxs-lookup"><span data-stu-id="d2098-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="d2098-108">重新定型后，新模型将图像组织成较大类别。</span><span class="sxs-lookup"><span data-stu-id="d2098-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="d2098-109">从头开始定型[图像分类](https://en.wikipedia.org/wiki/Outline_of_object_recognition)模型需要设置数百万个参数、大量已标记的定型数据和海量计算资源（数百个 GPU 小时）。</span><span class="sxs-lookup"><span data-stu-id="d2098-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="d2098-110">虽然不如从头开始定型自定义模型有效，但借助迁移学习，可以通过处理数千张图像（与数百万张已标记的图像相比）来简化此过程，并非常快速地生成自定义模型（在没有 GPU 的计算机上一小时内完成）。</span><span class="sxs-lookup"><span data-stu-id="d2098-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="d2098-111">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="d2098-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d2098-112">了解问题</span><span class="sxs-lookup"><span data-stu-id="d2098-112">Understand the problem</span></span>
> * <span data-ttu-id="d2098-113">重用和优化预定型模型</span><span class="sxs-lookup"><span data-stu-id="d2098-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d2098-114">分类图像</span><span class="sxs-lookup"><span data-stu-id="d2098-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="d2098-115">什么是迁移学习？</span><span class="sxs-lookup"><span data-stu-id="d2098-115">What is transfer learning?</span></span>

<span data-ttu-id="d2098-116">如果可以重用已预定型的模型来解决类似问题，并重新定型此模型的所有层或部分层来解决问题，那该有多好！</span><span class="sxs-lookup"><span data-stu-id="d2098-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="d2098-117">重用部分已定型的模型来生成新模型的技术称为[迁移学习](https://en.wikipedia.org/wiki/Transfer_learning)。</span><span class="sxs-lookup"><span data-stu-id="d2098-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="d2098-118">图像分类示例概述</span><span class="sxs-lookup"><span data-stu-id="d2098-118">Image classification sample overview</span></span>

<span data-ttu-id="d2098-119">此示例是一个控制台应用，使用 ML.NET 并通过重用预定型模型来生成图像分类器，以对定型数据很少的图像进行分类。</span><span class="sxs-lookup"><span data-stu-id="d2098-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="d2098-120">可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存储库中找到本教程的源代码。</span><span class="sxs-lookup"><span data-stu-id="d2098-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="d2098-121">请注意在本教程中，.NET 项目配置默认面向 .NET core 2.2。</span><span class="sxs-lookup"><span data-stu-id="d2098-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2098-122">系统必备</span><span class="sxs-lookup"><span data-stu-id="d2098-122">Prerequisites</span></span>

* <span data-ttu-id="d2098-123">安装了“.NET Core 跨平台开发”工作负载的 [Visual Studio 2017 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="d2098-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="d2098-124">Microsoft.ML 1.0.0 Nuget 包</span><span class="sxs-lookup"><span data-stu-id="d2098-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d2098-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget 包</span><span class="sxs-lookup"><span data-stu-id="d2098-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d2098-126">Microsoft.ML.TensorFlow 0.12.0 Nuget 包</span><span class="sxs-lookup"><span data-stu-id="d2098-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="d2098-127">教程资产目录 .ZIP 文件</span><span class="sxs-lookup"><span data-stu-id="d2098-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="d2098-128">InceptionV1 机器学习模型</span><span class="sxs-lookup"><span data-stu-id="d2098-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d2098-129">选择适当的机器学习任务</span><span class="sxs-lookup"><span data-stu-id="d2098-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d2098-130">[深度学习](https://en.wikipedia.org/wiki/Deep_learning)是机器学习的一部分，颠覆了计算机视觉和语音识别等领域。</span><span class="sxs-lookup"><span data-stu-id="d2098-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="d2098-131">深度学习模型是使用包含多个学习层的大量[已标记的数据](https://en.wikipedia.org/wiki/Labeled_data)和[神经网络](https://en.wikipedia.org/wiki/Artificial_neural_network)来定型。</span><span class="sxs-lookup"><span data-stu-id="d2098-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="d2098-132">深度学习：</span><span class="sxs-lookup"><span data-stu-id="d2098-132">Deep learning:</span></span>

* <span data-ttu-id="d2098-133">执行计算机视觉等一些任务的效果更好。</span><span class="sxs-lookup"><span data-stu-id="d2098-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="d2098-134">处理大量数据的效果好。</span><span class="sxs-lookup"><span data-stu-id="d2098-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="d2098-135">图像分类是常见的机器学习任务，可便于自动将图像分类为多个类别，比如：</span><span class="sxs-lookup"><span data-stu-id="d2098-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="d2098-136">检测图像中是否有人脸。</span><span class="sxs-lookup"><span data-stu-id="d2098-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="d2098-137">检测是猫还是狗。</span><span class="sxs-lookup"><span data-stu-id="d2098-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="d2098-138">或者在以下图像中，确定图像是食物、玩具还是家用电器：</span><span class="sxs-lookup"><span data-stu-id="d2098-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="d2098-139">![披萨图像](./media/image-classification/220px-Pepperoni_pizza.jpg)
![泰迪熊图像](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![烤面包机图像](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2098-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="d2098-140">上面的图像属于维基共享资源，并按如下方式进行属性化：</span><span class="sxs-lookup"><span data-stu-id="d2098-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="d2098-141">“220px-Pepperoni_pizza.jpg”公有领域，[https://commons.wikimedia.org/w/index.php?curid=79505](https://commons.wikimedia.org/w/index.php?curid=79505 )</span><span class="sxs-lookup"><span data-stu-id="d2098-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="d2098-142">“119px-Nalle_-_a_small_brown_teddy_bear.jpg”作者为 [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - 独自拍摄，CC BY-SA 2.0，[https://commons.wikimedia.org/w/index.php?curid=48166](https://commons.wikimedia.org/w/index.php?curid=48166 )。</span><span class="sxs-lookup"><span data-stu-id="d2098-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="d2098-143">“193px-Broodrooster.jpg”作者为 [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - 自有作品，CC BY-SA 3.0，[https://commons.wikimedia.org/w/index.php?curid=27403](https://commons.wikimedia.org/w/index.php?curid=27403 )</span><span class="sxs-lookup"><span data-stu-id="d2098-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="d2098-144">迁移学习包括多种策略，如重新定型所有层策略  和倒数第二层策略  。</span><span class="sxs-lookup"><span data-stu-id="d2098-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="d2098-145">本教程将介绍并展示如何使用倒数第二层策略  。</span><span class="sxs-lookup"><span data-stu-id="d2098-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="d2098-146">倒数第二层策略  重用已预定型的模型来解决具体问题。</span><span class="sxs-lookup"><span data-stu-id="d2098-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="d2098-147">然后，此策略重新定型这个模型的最后一层来解决新问题。</span><span class="sxs-lookup"><span data-stu-id="d2098-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="d2098-148">重用预定型模型作为新模型的一部分将节省大量时间和资源。</span><span class="sxs-lookup"><span data-stu-id="d2098-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="d2098-149">图像分类模型重用 [Inception 模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)，这是对 `ImageNet` 数据集定型的热门图像识别模型，其中 TensorFlow 模型尝试将所有图像分类为 1000 个类别，如“雨伞”、“针织衫”和“洗碗机”。</span><span class="sxs-lookup"><span data-stu-id="d2098-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="d2098-150">`Inception v1 model` 可以分类为[深度卷积神经网络](https://en.wikipedia.org/wiki/Convolutional_neural_network)，执行艰难视觉识别任务的效果合理，在一些领域中匹敌或超过人为绩效。</span><span class="sxs-lookup"><span data-stu-id="d2098-150">The `Inception v1 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="d2098-151">此模型/算法是由多个研究人员根据以下原始文章开发的：[“重新思考计算机视觉的 Inception 体系结构”，作者为 Szegedy 以及其他人](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="d2098-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="d2098-152">由于 `Inception model` 已对数千个不同图像进行过预定型，因此其中包含图像识别所需的[图像特征](https://en.wikipedia.org/wiki/Feature_(computer_vision))。</span><span class="sxs-lookup"><span data-stu-id="d2098-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="d2098-153">较低图像特征层识别简单特征（如边缘），较高层识别更复杂的特征（如形状）。</span><span class="sxs-lookup"><span data-stu-id="d2098-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="d2098-154">最后一层对更小的数据集进行定型，因为你是从已了解如何分类图像的预定型模型入手。</span><span class="sxs-lookup"><span data-stu-id="d2098-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="d2098-155">由于模型允许分类为超过两个类别，因此这是[多类别分类器](../resources/tasks.md#multiclass-classification)示例。</span><span class="sxs-lookup"><span data-stu-id="d2098-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="d2098-156">`TensorFlow` 是热门深度学习和机器学习工具包，可用于定型深度神经网络（和常规数值计算），并在 ML.NET 中实现为 `transformer`。</span><span class="sxs-lookup"><span data-stu-id="d2098-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="d2098-157">在本教程中，它用于重用 `Inception model`。</span><span class="sxs-lookup"><span data-stu-id="d2098-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="d2098-158">如下图中所示，在 .NET Core 或 .NET Framework 应用中添加对 ML.NET NuGet 包的引用。</span><span class="sxs-lookup"><span data-stu-id="d2098-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="d2098-159">实际上，ML.NET 包含并引用本机 `TensorFlow` 库，可用于编写代码来加载已定型的现有 `TensorFlow` 模型文件以进行评分。</span><span class="sxs-lookup"><span data-stu-id="d2098-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![TensorFlow 转换 ML.NET 体系结构图](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="d2098-161">`Inception model` 定型为将图像分类为 1000 个类别，但你只需要在更小的类别集中分类图像。</span><span class="sxs-lookup"><span data-stu-id="d2098-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="d2098-162">输入 `transfer learning` 的 `transfer` 部分。</span><span class="sxs-lookup"><span data-stu-id="d2098-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="d2098-163">可以将 `Inception model` 的识别和分类图像功能迁移到自定义图像分类器的新受限类别。</span><span class="sxs-lookup"><span data-stu-id="d2098-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="d2098-164">你将使用以下三个类别来重新定型此模型中的最后一层：</span><span class="sxs-lookup"><span data-stu-id="d2098-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="d2098-165">食物</span><span class="sxs-lookup"><span data-stu-id="d2098-165">Food</span></span>
* <span data-ttu-id="d2098-166">玩具</span><span class="sxs-lookup"><span data-stu-id="d2098-166">Toy</span></span>
* <span data-ttu-id="d2098-167">家用电器</span><span class="sxs-lookup"><span data-stu-id="d2098-167">Appliance</span></span>

<span data-ttu-id="d2098-168">你的层使用[多项逻辑回归算法](https://en.wikipedia.org/wiki/Multinomial_logistic_regression)尽可能快地找到正确的类别。</span><span class="sxs-lookup"><span data-stu-id="d2098-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="d2098-169">此算法使用概率来确定答案，向正确类别提供值 1，向其他类别提供值 0，从而进行分类。</span><span class="sxs-lookup"><span data-stu-id="d2098-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="d2098-170">数据集</span><span class="sxs-lookup"><span data-stu-id="d2098-170">DataSet</span></span>

<span data-ttu-id="d2098-171">数据源有两个：`.tsv` 文件和图像文件。</span><span class="sxs-lookup"><span data-stu-id="d2098-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="d2098-172">`tags.tsv` 文件包含两个列：第一列定义为 `ImagePath`，第二列是与图像对应的 `Label`。</span><span class="sxs-lookup"><span data-stu-id="d2098-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="d2098-173">下面的示例文件没有标题行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d2098-173">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="d2098-174">定型图像和测试图像位于下载 zip 文件的资产文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d2098-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="d2098-175">这些图像属于维基共享资源。</span><span class="sxs-lookup"><span data-stu-id="d2098-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="d2098-176">[维基共享资源](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208)，免费媒体存储库。 </span><span class="sxs-lookup"><span data-stu-id="d2098-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="d2098-177">检索时间：2018 年 10 月 17 日 10:48 检索位置：</span><span class="sxs-lookup"><span data-stu-id="d2098-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="d2098-178">创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="d2098-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d2098-179">创建项目</span><span class="sxs-lookup"><span data-stu-id="d2098-179">Create a project</span></span>

1. <span data-ttu-id="d2098-180">创建名为“TransferLearningTF”的 **.NET Core 控制台应用程序**。</span><span class="sxs-lookup"><span data-stu-id="d2098-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="d2098-181">安装“Microsoft.ML NuGet 包”  ：</span><span class="sxs-lookup"><span data-stu-id="d2098-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d2098-182">在“解决方案资源管理器”中，右键单击项目，然后选择“管理 NuGet 包”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d2098-183">选择“nuget.org”作为“包源”，选择“浏览”选项卡，再搜索“Microsoft.ML”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="d2098-184">单击“版本”下拉列表，选择列表中的“1.0.0”包，然后选择“安装”按钮    。</span><span class="sxs-lookup"><span data-stu-id="d2098-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d2098-185">选择“预览更改”  对话框上的“确定”  按钮，如果你同意所列包的许可条款，则选择“接受许可”  对话框上的“我接受”  按钮。</span><span class="sxs-lookup"><span data-stu-id="d2098-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="d2098-186">对 **Microsoft.ML.ImageAnalytics v1.0.0** 和 **Microsoft.ML.TensorFlow v0.12.0** 重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="d2098-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="d2098-187">准备数据</span><span class="sxs-lookup"><span data-stu-id="d2098-187">Prepare your data</span></span>

1. <span data-ttu-id="d2098-188">下载并解压缩[项目资产目录 zip 文件](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)。</span><span class="sxs-lookup"><span data-stu-id="d2098-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="d2098-189">将“`assets`”目录复制到“TransferLearningTF”  项目目录中。</span><span class="sxs-lookup"><span data-stu-id="d2098-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="d2098-190">此目录及其子目录包含本教程所需的数据和支持文件（Inception 模型除外，将在下一步中下载并添加此模型）。</span><span class="sxs-lookup"><span data-stu-id="d2098-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="d2098-191">下载并解压缩 [Inception 模型](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)。</span><span class="sxs-lookup"><span data-stu-id="d2098-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="d2098-192">将刚刚解压缩的“`inception5h`”目录的内容复制到 TransferLearningTF  项目的“`assets\inputs-train\inception`”目录中。</span><span class="sxs-lookup"><span data-stu-id="d2098-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="d2098-193">此目录包含本教程所需的模型和其他支持文件，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="d2098-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Inception 目录内容](./media/image-classification/inception-files.png)

5. <span data-ttu-id="d2098-195">在“解决方案资源管理器”中，右键单击资产目录和子目录中的每个文件，再选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="d2098-196">在“高级”下，将“复制到输出目录”的值更改为“如果较新则复制”    。</span><span class="sxs-lookup"><span data-stu-id="d2098-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d2098-197">创建类和定义路径</span><span class="sxs-lookup"><span data-stu-id="d2098-197">Create classes and define paths</span></span>

<span data-ttu-id="d2098-198">将以下附加的 `using` 语句添加到“Program.cs”  文件顶部：</span><span class="sxs-lookup"><span data-stu-id="d2098-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="d2098-199">创建全局字段，用于保留各种资产的路径，以及 `LabelTokey`、`ImageReal` 和 `PredictedLabelValue` 的全局变量：</span><span class="sxs-lookup"><span data-stu-id="d2098-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="d2098-200">`_assetsPath` 包含资产的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="d2098-201">`_trainTagsTsv` 包含定型图像数据标记 tsv 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="d2098-202">`_predictTagsTsv` 包含预测图像数据标记 tsv 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="d2098-203">`_trainImagesFolder` 包含用于定型模型的图像的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="d2098-204">`_predictImagesFolder` 包含已定型的模型要分类的图像的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="d2098-205">`_inceptionPb` 包含要重用于重新定型模型的预定型 Inception 模型的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="d2098-206">`_inputImageClassifierZip` 包含从中加载已定型的模型的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="d2098-207">`_outputImageClassifierZip` 具有在其中保存定型模型的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="d2098-208">`LabelTokey` 是映射到键的 `Label` 值。</span><span class="sxs-lookup"><span data-stu-id="d2098-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="d2098-209">`ImageReal` 是包含预测出的图像值的列。</span><span class="sxs-lookup"><span data-stu-id="d2098-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="d2098-210">`PredictedLabelValue` 是包含预测出的标签值的列。</span><span class="sxs-lookup"><span data-stu-id="d2098-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="d2098-211">将以下代码添加到 `Main` 方法正上方的行中以指定这些路径和其他变量：</span><span class="sxs-lookup"><span data-stu-id="d2098-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="d2098-212">为输入数据和预测结果创建一些类。</span><span class="sxs-lookup"><span data-stu-id="d2098-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="d2098-213">向项目添加一个新类：</span><span class="sxs-lookup"><span data-stu-id="d2098-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="d2098-214">在“解决方案资源管理器”  中，右键单击项目，然后选择“添加”   > “新项”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d2098-215">在“添加新项”  对话框中，选择“类”  ，并将“名称”  字段更改为“ImageData.cs”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="d2098-216">然后，选择“添加”  按钮。</span><span class="sxs-lookup"><span data-stu-id="d2098-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d2098-217">此时，ImageData.cs  文件在代码编辑器中打开。</span><span class="sxs-lookup"><span data-stu-id="d2098-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2098-218">将下面的 `using` 语句添加到 ImageData.cs  顶部：</span><span class="sxs-lookup"><span data-stu-id="d2098-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="d2098-219">删除现有类定义，并将 `ImageData` 类的以下代码添加到 ImageData.cs  文件中：</span><span class="sxs-lookup"><span data-stu-id="d2098-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="d2098-220">`ImageData` 是输入图像数据类，包含以下 <xref:System.String> 字段：</span><span class="sxs-lookup"><span data-stu-id="d2098-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="d2098-221">`ImagePath` 包含图像文件名。</span><span class="sxs-lookup"><span data-stu-id="d2098-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="d2098-222">`Label` 包含图像标签值。</span><span class="sxs-lookup"><span data-stu-id="d2098-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="d2098-223">向项目添加 `ImagePrediction` 的新类：</span><span class="sxs-lookup"><span data-stu-id="d2098-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="d2098-224">在“解决方案资源管理器”  中，右键单击项目，然后选择“添加”   > “新项”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d2098-225">在“添加新项”  对话框中，选择“类”  ，并将“名称”  字段更改为“ImagePrediction.cs”  。</span><span class="sxs-lookup"><span data-stu-id="d2098-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="d2098-226">然后，选择“添加”  按钮。</span><span class="sxs-lookup"><span data-stu-id="d2098-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d2098-227">此时，ImagePrediction.cs  文件在代码编辑器中打开。</span><span class="sxs-lookup"><span data-stu-id="d2098-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="d2098-228">删除 ImagePrediction.cs  顶部的 `System.Collections.Generic` 和 `System.Text` `using` 语句：</span><span class="sxs-lookup"><span data-stu-id="d2098-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="d2098-229">删除现有类定义，并将包含 `ImagePrediction` 类的以下代码添加到 ImagePrediction.cs  文件中：</span><span class="sxs-lookup"><span data-stu-id="d2098-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="d2098-230">`ImagePrediction` 是图像预测类，包含以下字段：</span><span class="sxs-lookup"><span data-stu-id="d2098-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="d2098-231">`Score` 包含给定图像分类的置信度百分比。</span><span class="sxs-lookup"><span data-stu-id="d2098-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="d2098-232">`PredictedLabelValue` 包含预测出的图像分类标签的值。</span><span class="sxs-lookup"><span data-stu-id="d2098-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="d2098-233">`ImagePrediction` 是在定型模型后用于预测的类。</span><span class="sxs-lookup"><span data-stu-id="d2098-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="d2098-234">它包含图像路径的 `string` (`ImagePath`)。</span><span class="sxs-lookup"><span data-stu-id="d2098-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="d2098-235">`Label` 用于重用和重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="d2098-236">`PredictedLabelValue` 在预测和评估过程中使用。</span><span class="sxs-lookup"><span data-stu-id="d2098-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="d2098-237">对于计算，将使用带定型数据的输入、预测值和模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="d2098-238">执行所有 ML.NET 操作都是从 [MLContext 类](xref:Microsoft.ML.MLContext)开始，初始化 `mlContext` 可创建一个新的 ML.NET 环境，可在模型创建工作流对象之间共享该环境。</span><span class="sxs-lookup"><span data-stu-id="d2098-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d2098-239">从概念上讲，它与实体框架中的 `DBContext` 类似。</span><span class="sxs-lookup"><span data-stu-id="d2098-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d2098-240">在 Main 中初始化变量</span><span class="sxs-lookup"><span data-stu-id="d2098-240">Initialize variables in Main</span></span>

<span data-ttu-id="d2098-241">使用 `MLContext` 的新实例初始化 `mlContext` 变量。</span><span class="sxs-lookup"><span data-stu-id="d2098-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="d2098-242">用下面 `Main` 方法中的代码替换 `Console.WriteLine("Hello World!")` 行：</span><span class="sxs-lookup"><span data-stu-id="d2098-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="d2098-243">创建默认参数的结构</span><span class="sxs-lookup"><span data-stu-id="d2098-243">Create a struct for default parameters</span></span>

<span data-ttu-id="d2098-244">需要传入 Inception 模型的多个默认参数。</span><span class="sxs-lookup"><span data-stu-id="d2098-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="d2098-245">紧跟在 `Main()` 方法后面，使用以下代码创建结构，以将默认参数值映射到易记名称：</span><span class="sxs-lookup"><span data-stu-id="d2098-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="d2098-246">创建显示实用工具方法</span><span class="sxs-lookup"><span data-stu-id="d2098-246">Create a display utility method</span></span>

<span data-ttu-id="d2098-247">由于将多次显示图像数据和相关预测，请创建显示实用工具方法，用于处理图像和预测结果的显示。</span><span class="sxs-lookup"><span data-stu-id="d2098-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="d2098-248">`DisplayResults()` 方法执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2098-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="d2098-249">显示预测结果。</span><span class="sxs-lookup"><span data-stu-id="d2098-249">Displays the predicted results.</span></span>

<span data-ttu-id="d2098-250">紧跟在 `InceptionSettings` 结构后面，使用下面的代码创建 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="d2098-251">`Transform()` 方法在 `ImagePrediction` 中填充 `ImagePath` 以及预测的字段。</span><span class="sxs-lookup"><span data-stu-id="d2098-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="d2098-252">随着 ML.NET 进程继续执行，每个组件会添加列，这让显示结果变得轻松：</span><span class="sxs-lookup"><span data-stu-id="d2098-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="d2098-253">将在两个图像分类方法中调用 `DisplayResults()` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2098-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="d2098-254">创建 .tsv 文件实用工具方法</span><span class="sxs-lookup"><span data-stu-id="d2098-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="d2098-255">`ReadFromTsv()` 方法执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2098-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="d2098-256">读取图像数据 `tags.tsv` 文件。</span><span class="sxs-lookup"><span data-stu-id="d2098-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="d2098-257">将文件路径添加到图像文件名中。</span><span class="sxs-lookup"><span data-stu-id="d2098-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="d2098-258">将文件数据加载到 IEnumerable`ImageData` 对象中。</span><span class="sxs-lookup"><span data-stu-id="d2098-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="d2098-259">使用下面的代码紧随 `PairAndDisplayResults()` 方法后创建 `ReadFromTsv()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="d2098-260">下面的代码分析整个 `tags.tsv` 文件，以将文件路径添加到 `ImagePath` 属性的图像文件名中，并将它和 `Label` 加载到 `ImageData` 对象中。</span><span class="sxs-lookup"><span data-stu-id="d2098-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="d2098-261">将它添加为 `ReadFromTsv()` 方法的第一行。</span><span class="sxs-lookup"><span data-stu-id="d2098-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="d2098-262">必须有完全限定的文件路径，才能显示预测结果。</span><span class="sxs-lookup"><span data-stu-id="d2098-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="d2098-263">ML.NET 中包含三个主要概念：[数据](../resources/glossary.md#data)、[转换器](../resources/glossary.md#transformer)和[估算器](../resources/glossary.md#estimator)。</span><span class="sxs-lookup"><span data-stu-id="d2098-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="d2098-264">重用和优化预定型模型</span><span class="sxs-lookup"><span data-stu-id="d2098-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="d2098-265">将以下调用添加到 `ReuseAndTuneInceptionModel()` 方法作为 `Main()` 方法的下一行代码：</span><span class="sxs-lookup"><span data-stu-id="d2098-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="d2098-266">`ReuseAndTuneInceptionModel()` 方法执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2098-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="d2098-267">加载数据</span><span class="sxs-lookup"><span data-stu-id="d2098-267">Loads the data</span></span>
* <span data-ttu-id="d2098-268">提取并转换数据。</span><span class="sxs-lookup"><span data-stu-id="d2098-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="d2098-269">对 TensorFlow 模型评分。</span><span class="sxs-lookup"><span data-stu-id="d2098-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="d2098-270">优化（重新定型）模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="d2098-271">显示模型结果。</span><span class="sxs-lookup"><span data-stu-id="d2098-271">Displays model results.</span></span>
* <span data-ttu-id="d2098-272">评估模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-272">Evaluates the model.</span></span>
* <span data-ttu-id="d2098-273">返回模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-273">Returns the model.</span></span>

<span data-ttu-id="d2098-274">紧跟在 `InceptionSettings` 结构后面且恰好在 `DisplayResults()` 方法前面，使用以下代码创建 `ReuseAndTuneInceptionModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="d2098-275">加载数据</span><span class="sxs-lookup"><span data-stu-id="d2098-275">Load the data</span></span>

<span data-ttu-id="d2098-276">ML.NET 中的数据表示为 [IDataView 类](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="d2098-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d2098-277">`IDataView` 是用于描述表格数据（数字和文本）的一种灵活且有效的方法。</span><span class="sxs-lookup"><span data-stu-id="d2098-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d2098-278">可从文本文件或实时（例如，SQL 数据库或日志文件）将数据加载到 `IDataView` 对象。</span><span class="sxs-lookup"><span data-stu-id="d2098-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="d2098-279">使用 `MLContext.Data.LoadFromTextFile` 包装器加载数据。</span><span class="sxs-lookup"><span data-stu-id="d2098-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="d2098-280">将以下代码作为下一行添加到 `ReuseAndTuneInceptionModel()` 方法中：</span><span class="sxs-lookup"><span data-stu-id="d2098-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="d2098-281">提取功能和转换数据</span><span class="sxs-lookup"><span data-stu-id="d2098-281">Extract Features and transform the data</span></span>

<span data-ttu-id="d2098-282">预处理和清除数据任务至关重要，需要首先执行才能将数据集有效地用于机器学习。</span><span class="sxs-lookup"><span data-stu-id="d2098-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="d2098-283">在没有这些建模任务的情况下使用数据会产生误导性结果。</span><span class="sxs-lookup"><span data-stu-id="d2098-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="d2098-284">机器学习算法理解[特征化](../resources/glossary.md#feature)数据，因此在处理深度神经网络时，必须将图像调整为网络所需的格式。</span><span class="sxs-lookup"><span data-stu-id="d2098-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="d2098-285">该格式是[数值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="d2098-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="d2098-286">定型和评估后，预测“标签”  列值。</span><span class="sxs-lookup"><span data-stu-id="d2098-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="d2098-287">由于使用的是预定型模型，因此使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法将字段映射到新模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="d2098-288">此方法会将 `Label` 转换为数值键类型 (`LabelTokey`) 列，并将它添加为新数据集列：将此命名为 `estimator`，因为还会向它添加定型程序。</span><span class="sxs-lookup"><span data-stu-id="d2098-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="d2098-289">添加下一个代码行：</span><span class="sxs-lookup"><span data-stu-id="d2098-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="d2098-290">图像处理估算器使用预定型[深度神经网络 (DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) 特征提取器来提取特征。</span><span class="sxs-lookup"><span data-stu-id="d2098-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="d2098-291">处理深度神经网络时，将图像调整为所需的网络格式。</span><span class="sxs-lookup"><span data-stu-id="d2098-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="d2098-292">正因为此，你使用多个图像转换将图像数据转换为模型所需的格式：</span><span class="sxs-lookup"><span data-stu-id="d2098-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="d2098-293">`LoadImages` 转换图像作为位图类型加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="d2098-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="d2098-294">`ResizeImages` 转换可重设图像大小，因为预定型模型有已定义的输入图像宽度和高度。</span><span class="sxs-lookup"><span data-stu-id="d2098-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="d2098-295">`ExtractPixels` 转换可提取输入图像中的像素，并将它们转换为数值向量。</span><span class="sxs-lookup"><span data-stu-id="d2098-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="d2098-296">将这些图像转换添加为接下来的几行代码：</span><span class="sxs-lookup"><span data-stu-id="d2098-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="d2098-297">`LoadTensorFlowModel` 是一种便捷方法，允许加载一次 `TensorFlow` 模型，然后使用 `ScoreTensorFlowModel` 创建 `TensorFlowEstimator`。</span><span class="sxs-lookup"><span data-stu-id="d2098-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="d2098-298">`ScoreTensorFlowModel` 提取指定输出（`Inception model` 的图像特征 `softmax2_pre_activation`），并使用预定型 `TensorFlow` 模型对数据集进行评分。</span><span class="sxs-lookup"><span data-stu-id="d2098-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="d2098-299">`softmax2_pre_activation` 协助模型确定图像属于哪个类别。</span><span class="sxs-lookup"><span data-stu-id="d2098-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="d2098-300">`softmax2_pre_activation` 返回图像每个类别的概率，所有这些概率的总和必须为 1。</span><span class="sxs-lookup"><span data-stu-id="d2098-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="d2098-301">它假设图像仅属于一个类别，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="d2098-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="d2098-302">类</span><span class="sxs-lookup"><span data-stu-id="d2098-302">Class</span></span>         | <span data-ttu-id="d2098-303">概率</span><span class="sxs-lookup"><span data-stu-id="d2098-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="d2098-304">0.001</span><span class="sxs-lookup"><span data-stu-id="d2098-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="d2098-305">0.95</span><span class="sxs-lookup"><span data-stu-id="d2098-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="d2098-306">0.06</span><span class="sxs-lookup"><span data-stu-id="d2098-306">0.06</span></span>         |

<span data-ttu-id="d2098-307">使用以下代码行将 `TensorFlowTransform` 追加到 `estimator`：</span><span class="sxs-lookup"><span data-stu-id="d2098-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="d2098-308">选择定型算法</span><span class="sxs-lookup"><span data-stu-id="d2098-308">Choose a training algorithm</span></span>

<span data-ttu-id="d2098-309">若要添加定型算法，请调用 `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` 包装器方法。</span><span class="sxs-lookup"><span data-stu-id="d2098-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="d2098-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) 追加到 `estimator` 中，并接受 Inception 图像特征 (`softmax2_pre_activation`) 和 `Label` 输入参数，以便从历史数据中学习。</span><span class="sxs-lookup"><span data-stu-id="d2098-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="d2098-311">使用以下代码添加定型程序：</span><span class="sxs-lookup"><span data-stu-id="d2098-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="d2098-312">还需要将 `predictedlabel` 映射到 `predictedlabelvalue`：</span><span class="sxs-lookup"><span data-stu-id="d2098-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="d2098-313">`Fit()` 方法通过转换数据集并应用训练来训练模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="d2098-314">在 `ReuseAndTuneInceptionModel()` 方法中添加以下代码作为下一行代码，使模型拟合训练数据集，并返回经过训练的模型：</span><span class="sxs-lookup"><span data-stu-id="d2098-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="d2098-315">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法对测试数据集的多个提供的输入行进行预测。</span><span class="sxs-lookup"><span data-stu-id="d2098-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="d2098-316">将以下代码添加到 `ReuseAndTuneInceptionModel()` 以转换 `Training` 数据：</span><span class="sxs-lookup"><span data-stu-id="d2098-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="d2098-317">为了更方便显示，将图像数据和预测 `DataViews` 转换为强类型 `IEnumerables`，以供配对。</span><span class="sxs-lookup"><span data-stu-id="d2098-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="d2098-318">为此，通过下面的代码使用 `MLContext.CreateEnumerable()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="d2098-319">添加以下代码作为 `ReuseAndTuneInceptionModel()` 方法的下几行来显示数据和预测结果：</span><span class="sxs-lookup"><span data-stu-id="d2098-319">Add the following code to display your data and predictions as the next lines in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="d2098-320">在你设置预测后，[Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法便能：</span><span class="sxs-lookup"><span data-stu-id="d2098-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="d2098-321">评估模型（将预测出的值与实际数据集 `Labels` 进行比较）。</span><span class="sxs-lookup"><span data-stu-id="d2098-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="d2098-322">返回模型性能指标。</span><span class="sxs-lookup"><span data-stu-id="d2098-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="d2098-323">将以下代码作为下一行添加到 `ReuseAndTuneInceptionModel()` 方法中：</span><span class="sxs-lookup"><span data-stu-id="d2098-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="d2098-324">下面是图像分类评估指标：</span><span class="sxs-lookup"><span data-stu-id="d2098-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="d2098-325">`Log-loss` - 请参阅[对数损失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="d2098-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="d2098-326">通常会希望对数损失尽可能接近 0。</span><span class="sxs-lookup"><span data-stu-id="d2098-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="d2098-327">`Per class Log-loss`。</span><span class="sxs-lookup"><span data-stu-id="d2098-327">`Per class Log-loss`.</span></span> <span data-ttu-id="d2098-328">建议每类别的对数损失尽可能接近 0。</span><span class="sxs-lookup"><span data-stu-id="d2098-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="d2098-329">使用下面的代码显示指标、共享结果，然后处理它们：</span><span class="sxs-lookup"><span data-stu-id="d2098-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="d2098-330">添加以下代码，将经过训练的模型作为下一行代码返回：</span><span class="sxs-lookup"><span data-stu-id="d2098-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="d2098-331">使用已加载的模型来分类图像</span><span class="sxs-lookup"><span data-stu-id="d2098-331">Classify images with a loaded model</span></span>

<span data-ttu-id="d2098-332">将以下 `ClassifyImages()` 方法调用添加为 `Main` 方法的下一行代码：</span><span class="sxs-lookup"><span data-stu-id="d2098-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="d2098-333">`ClassifyImages()` 方法执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2098-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="d2098-334">将 .TSV 文件读取到 `IEnumerable` 中。</span><span class="sxs-lookup"><span data-stu-id="d2098-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="d2098-335">根据测试数据预测图像分类。</span><span class="sxs-lookup"><span data-stu-id="d2098-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="d2098-336">紧跟在 `ReuseAndTuneInceptionModel()` 方法后面且恰好在 `PairAndDisplayResults()` 方法前面，使用以下代码创建 `ClassifyImages()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d2098-337">首先，调用 `ReadFromTsv()` 方法来创建 `IEnumerable<ImageData>` 类，其中包含每个 `ImagePath` 的完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="d2098-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="d2098-338">必须有此文件路径，才能配对数据和预测结果。</span><span class="sxs-lookup"><span data-stu-id="d2098-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="d2098-339">还需要将 `IEnumerable<ImageData>` 类转换为将用于预测的 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="d2098-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="d2098-340">将以下代码添加为 `ClassifyImages()` 方法的接下来两行代码：</span><span class="sxs-lookup"><span data-stu-id="d2098-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="d2098-341">如同之前处理训练图像数据一样，使用传入模型的 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法预测测试图像数据的类别。</span><span class="sxs-lookup"><span data-stu-id="d2098-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="d2098-342">将以下代码添加到预测结果的 `ClassifyImages()` 方法，并将 `predictions` `IDataView` 转换为 `IEnumerable` 以供配对和显示：</span><span class="sxs-lookup"><span data-stu-id="d2098-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="d2098-343">若要配对和显示测试图像数据和预测结果，请将以下代码添加为 `ClassifyImages()` 方法的下一行，以调用之前创建的 `DisplayResults()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="d2098-344">使用已加载的模型来分类单张图像</span><span class="sxs-lookup"><span data-stu-id="d2098-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="d2098-345">将以下 `ClassifySingleImage()` 方法调用添加为 `Main` 方法的下一行代码：</span><span class="sxs-lookup"><span data-stu-id="d2098-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="d2098-346">`ClassifySingleImage()` 方法执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2098-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="d2098-347">加载 `ImageData` 实例。</span><span class="sxs-lookup"><span data-stu-id="d2098-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="d2098-348">根据测试数据预测图像分类。</span><span class="sxs-lookup"><span data-stu-id="d2098-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="d2098-349">紧跟在 `ClassifyImages()` 方法后面且恰好在 `PairAndDisplayResults()` 方法前面，使用以下代码创建 `ClassifySingleImage()` 方法：</span><span class="sxs-lookup"><span data-stu-id="d2098-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d2098-350">首先，创建 `ImageData` 类，其中包含单个 `ImagePath` 的完全限定的路径和图像文件名。</span><span class="sxs-lookup"><span data-stu-id="d2098-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="d2098-351">将以下代码添加为 `ClassifySingleImage()` 方法的接下来几行：</span><span class="sxs-lookup"><span data-stu-id="d2098-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="d2098-352">[PredictionEngine 类](xref:Microsoft.ML.PredictionEngine%602)是对单个数据实例执行预测的简便 API。</span><span class="sxs-lookup"><span data-stu-id="d2098-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="d2098-353">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函数对单列数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="d2098-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="d2098-354">通过将以下代码添加到 `ClassifySingleImage()`，将 `imageData` 传递到 `PredictionEngine` 来预测图像类别：</span><span class="sxs-lookup"><span data-stu-id="d2098-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="d2098-355">`ClassifySingleImage()` 方法的下一行代码用于显示预测结果：</span><span class="sxs-lookup"><span data-stu-id="d2098-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="d2098-356">结果</span><span class="sxs-lookup"><span data-stu-id="d2098-356">Results</span></span>

<span data-ttu-id="d2098-357">按照上述步骤操作后，运行控制台应用 (Ctrl + F5)。</span><span class="sxs-lookup"><span data-stu-id="d2098-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d2098-358">结果应如以下输出所示。</span><span class="sxs-lookup"><span data-stu-id="d2098-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="d2098-359">你可能会看到警告或处理消息，为清楚起见，这些消息已从以下结果中删除。</span><span class="sxs-lookup"><span data-stu-id="d2098-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="d2098-360">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="d2098-360">Congratulations!</span></span> <span data-ttu-id="d2098-361">现已通过重用 ML.NET 中的预定型 `TensorFlow` 模型，成功生成图像分类机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="d2098-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="d2098-362">可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) 存储库中找到本教程的源代码。</span><span class="sxs-lookup"><span data-stu-id="d2098-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="d2098-363">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="d2098-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d2098-364">了解问题</span><span class="sxs-lookup"><span data-stu-id="d2098-364">Understand the problem</span></span>
> * <span data-ttu-id="d2098-365">重用和优化预定型模型</span><span class="sxs-lookup"><span data-stu-id="d2098-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d2098-366">使用已加载的模型来分类图像</span><span class="sxs-lookup"><span data-stu-id="d2098-366">Classify images with a loaded model</span></span>

<span data-ttu-id="d2098-367">请查看机器学习示例 GitHub 存储库，以探索扩展的图像分类示例。</span><span class="sxs-lookup"><span data-stu-id="d2098-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d2098-368">dotnet/machinelearning-samples GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="d2098-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
