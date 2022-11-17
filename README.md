# Does the GPU have an impact on the performance of deep learning approaches ?

This Readme.md file focuses on the reasons why deep learning algorithms exhibit performance differences when faced with different GPU versions, and corresponding solutions.

In general, it is common for many scholars focused on deep learning approaches to believe that the impact of graphics processing unit (GPU) on algorithms is limited to the speed of computing, but this is not the case.

As Moore's Law has evolved, GPUs have seen important improvements in both manufacturing process and computing performance, but this has also had an impact on the convergence of algorithms. For example, a deep learning algorithm running in an RTX2080 environment cannot be reproduced in an RTX3080 environment (the loss value converges quickly to Nan). This phenomenon demonstrates that the GPU changes the performance of the deep learning algorithm in addition to improving the computational rate of the algorithm. Meanwhile, a similar phenomenon was found by Pietrowski et al [1] in 2021, who concluded that machine learning algorithms trained on GPUs may contain fewer errors and produce better results compared to computing processes in a CPU environment. Obviously, this case contradicts the general perception that GPUs are only about acceleration and not about making training results better. In other words, if the essence of the GPU is only acceleration, then it should maintain the same results as the CPU's in order to be valid.

We will then discuss a few further questions: (1) what are the factors that cause performance to vary? ; (2) how do these factors affect algorithm performance? and (3) how can the experimental results be reproduced after updating the GPU?

Firstly, the GPU is a piece of hardware dedicated to processing graphics images, and its process is constantly being updated to bring about improvements in two areas: the total number of parallel threads available, and the efficiency of image read-write conversion. The combined effect of these two factors is a significant increase in the speed of the algorithm.The variation in the total number of parallel threads is not a core factor in the performance deviation, although it does create uncertainty in the convergence of the gradient of deep learning depending on the arrangement of the threads. In contrast, the efficiency of image read/write conversions (computer-understandable binary conversions) may be the primary cause in which affects the deep learning algorithms.

If the GPU's process of loading, processing, and outputs is represented by the conversion of the image signal, it can be divided into two cases: (1) pixel values (loading) - pixel values (processing) - results (outputs) and (2) pixel values (loading) - pixel values converse to binary, processing, processing results inverse pixel values (processing) - results (outputs). If the former mode of processing is used, there is little probability that the different GPUs will cause performance deviations, because the pixel values will be fed directly into the algorithm whatever any GPU version. However, the fact which the accuracy deviation have already been existed in many practical applications indicates that the GPUs are operating via the mode (2) to process image information. Simultaneously, the operation mechanism of GPU like geometry processing, rasterisation processing, pixel conversion, and image rendering, also makes this viewpoint be confirmed. Consequently, the read-write conversion of the GPU may be the crucial reason for the performance deviation of the deep learning algorithms. The more advanced the GPU the higher the fidelity conversion for the true value will affect the algorithm results produced by the previous GPU versions.

How can the deep learning results obtained from older GPU releases be reproduced via advanced ones? No research has been reported on this issue, but in my personal experience with the deep learning algorithms, tuning the learning rate, Batchsize, or the parameters incorporating in neural network structure (such as convolutional kernels, stride) can be helpful in reproducing the results.

Reference:

[1]	M. Pietrowski, A. Gajda, T. Yamamoto, T. Kobayashi, L. Sinapayen, and E. Watanabe, “Impact of GPU uncertainty on the training of predictive deep neural networks,” 2021, [Online]. Available: http://arxiv.org/abs/2109.01451


This Readme.md file includes my personal views on the performance biases caused by GPU versions in deep learning algorithms. I'm looking forward to other peers contact me to discuss this issue. 

E-mail: wison@mail.bnu.edu.cn

