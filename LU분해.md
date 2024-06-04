# LU 분해
    선형대수학에서 행렬을 두개의 하삼각행렬 ( L ) 과 상삼각행렬 ( U )의 곱으로 분해하는 방법

    연립방정식을 풀거나 행렬의 역행렬을 구하는데 사용

### A = LU
    LU분해는 행렬 A를 두 행렬 L과 U의 곱으로 나타내는 것으로 가우스 소거법을 이용해서 U를 만들고 나머지는 LU분해를 이용해서 L을 구할 수 있습니다.

- 상삼각행렬
    - 주대각선 아래의 모근 원소가 0인 행렬
    
> 가우스 소거법을 이용하여 U를 구하고 A에 대해 사용된 소거 행렬들의 곱은 하삼각행렬 L을 형성 이 L은 U의 역행렬이 L임

A를 여러번 쓰면 A가 좋음
​
# 상삼각행렬로 변환하는 과정 (가우스 소거법 사용)

가우스 소거법을 사용하여 행렬을 상삼각형으로 변환하는 과정을 자세히 설명하겠습니다. 예시로 3x3 행렬을 사용합니다.

## 예시 행렬 \( A \)

$$
A = \begin{pmatrix}
2 & -1 & -2 \\
-4 & 6 & 3 \\
-4 & -2 & 8
\end{pmatrix}
$$

## 단계별 변환 과정

1. **첫 번째 열의 소거**

첫 번째 행의 첫 번째 원소(피벗)를 이용하여 첫 번째 열의 다른 원소를 0으로 만듭니다.

$$
\text{Pivot} = A[0, 0] = 2
$$

두 번째 행을 처리합니다:

$$
A[1] = A[1] - \left(\frac{A[1, 0]}{A[0, 0]}\right) \cdot A[0]
$$

$$
A[1] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} - \left(\frac{-4}{2}\right) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
$$

$$
A[1] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} + \begin{pmatrix} 4 & -2 & -4 \end{pmatrix} = \begin{pmatrix} 0 & 4 & -1 \end{pmatrix}
$$

세 번째 행을 처리합니다:

$$
A[2] = A[2] - \left(\frac{A[2, 0]}{A[0, 0]}\right) \cdot A[0]
$$

$$
A[2] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} - \left(\frac{-4}{2}\right) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
$$

$$
A[2] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} + \begin{pmatrix} 4 & -2 & -4 \end{pmatrix} = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix}
$$

현재 상태의 행렬 \( A \):

$$
A = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & -4 & 4
\end{pmatrix}
$$

2. **두 번째 열의 소거**

두 번째 행의 두 번째 원소(피벗)를 이용하여 두 번째 열의 아래 원소를 0으로 만듭니다.

$$
\text{Pivot} = A[1, 1] = 4
$$

세 번째 행을 처리합니다:

$$
A[2] = A[2] - \left(\frac{A[2, 1]}{A[1, 1]}\right) \cdot A[1]
$$

$$
A[2] = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix} - \left(\frac{-4}{4}\right) \cdot \begin{pmatrix} 0 & 4 & -1 \end{pmatrix}
$$

$$
A[2] = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix} + \begin{pmatrix} 0 & -4 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 & 5 \end{pmatrix}
$$

현재 상태의 행렬 \( A \):

$$
A = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & 0 & 5
\end{pmatrix}
$$

3. **결과: 상삼각행렬 \( U \)**

변환이 완료된 행렬 \( A \)는 상삼각형 형태의 행렬입니다. 이 행렬은 다음과 같습니다:

$$
U = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & 0 & 5
\end{pmatrix}
$$

이제 A에 대해 사용된 소거 행렬들의 곱은 하삼각행렬 L을 형성 이는 U의 역행렬임

첫 번째 피벗으로 2를 선택

2행 1열에 대해서 -2를 곱했기 때문에

$$
L = \begin{pmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
$$

3행 1열에 대해서 -2를 곱해서 

$$
L = \begin{pmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
-2 & 0 & 1
\end{pmatrix}
$$

현재 행렬 A는

$$
A = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & -4 & 4
\end{pmatrix}
$$

두 번째 피벗으로 4를 선택

3행 2열에 대해서 -1를 곱했기 때문에

$$
L = \begin{pmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
-2 & -1 & 1
\end{pmatrix}
$$

이렇게 해서 L이 나옴

최종적으로

$$
A = LU
$$

$$
\begin{pmatrix}
2 & -1 & -2 \\
-4 & 6 & 3 \\
-4 & -2 & 8
\end{pmatrix}

=

\begin{pmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
-2 & -1 & 1
\end{pmatrix}

\begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & 0 & 5
\end{pmatrix}
$$

이런 계산을 할 수 있음