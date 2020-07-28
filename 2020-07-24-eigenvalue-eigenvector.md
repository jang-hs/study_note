#### **고유값과 고유벡터**

_**definition**_

행렬 $\\rm{A}$ 가 $n\\times n$ 정방행렬일 때,

$$\\rm{A} \\underline{x} = \\lambda \\underline{x}$$

를 만족하는 _스칼라 $\\lambda$_와 _영이 아닌 벡터 $\\underline{x}$_가 존재하면 이러한 $\\lambda$를 행렬 $\\rm{A}$ 의 고유값, 벡터 $\\underline{x}$는 $\\lambda$에 대응하는 고유벡터라 한다.

-   계산 실례(출처 : [나무위키](%5Bhttps://ko.wikipedia.org/w/index.php?title=%EA%B3%A0%EC%9C%B3%EA%B0%92%EA%B3%BC_%EA%B3%A0%EC%9C%A0_%EB%B2%A1%ED%84%B0%5D(https://ko.wikipedia.org/w/index.php?title=%EA%B3%A0%EC%9C%B3%EA%B0%92%EA%B3%BC_%EA%B3%A0%EC%9C%A0_%EB%B2%A1%ED%84%B0)))

정사각 행렬의 고윳값과 고유 벡터는, 보통 (특히 행렬의 크기가 작은 경우) 고유 다항식을 통해 계산된다. 구체적으로, 고유 다항식을 구하고, 근을 구하고, 각 근에 대응하는 선형 방정식을 풀이한다. 큰 행렬에 대해서는 고유 다항식이 복잡해지므로 수치적 방법을 통해 근사적으로 구하기도 한다.

예를 들어, 실수 행렬

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a12ea509cd4add2be5f65c8e7fe82a303bce080e)

의 고윳값과 고유 벡터를 구하는 과정은 다음과 같다. 우선 $\\rm{A}$ 의 고유 다항식을 구한다.  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/ab5182809ae548628ea0cf3f651c9f628d30bdae)

근 $x = -1, 5$가 곧 $\\rm{A}$의 고유값이다. 고유값 $x = -1$에 대한 선형 방정식의 계수 행렬을 구한다.  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e5577ce17d1649c656349153c71f1e94486159f)

이에 대한 해공간은 다음과 같은 기저로 선형 생성됨을 알 수 있다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b020d01cc40e2d43458c3a63a1903f07ccfa3740)

비슷하게, 고유값 $x = 5$에 대한 선형 방정식의 계수 행렬은

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/43a5f813ce021b6839259a35df4e2d372d6a6e5d)

이고, 해공간의 기저는

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/97d8550485664a2bad49169fec1dd2c155296e33)

이다. $\\rm{A}$의 고유값과 고유 벡터는 이로써 명백해진다.

-   머신러닝에서 고유값의 활용
    -   머신러닝에서 고유값의 활용은 [이 글](https://brunch.co.kr/@chris-song/104)에 잘 정리가 되어있다. 크게 3가지 용법에 대해 소개하고 있다.
    -   주성분 분석(PCA) : 고차원의 데이터를 저차원으로 축소하는 고전적인 방법. 원 데이터를 적은 주성분 방향으로 투영하여 차원을 축소
    -   스펙트럼 클러스터링 : 스펙트럼 군집화는 행렬의 고유 벡터를 사용하여 군집을 찾는 방법.
    -   컴퓨터 비전의 관심 지점 감지

\+ (추가 예정) 행렬 $\\rm{A}\_{n\\times n}$에 대한 동치 명제