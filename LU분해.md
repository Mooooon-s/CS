# LU 분해
    선형대수학에서 행렬을 두개의 하삼각행렬 ( L ) 과 상삼각행렬 ( U )의 곱으로 분해하는 방법

    연립방정식을 풀거나 행렬의 역행렬을 구하는데 사용

### A = LU
    LU분해는 행렬 A를 두 행렬 L과 U의 곱으로 나타내는 것으로 가우스 소거법을 이용해서 L와 U를 만들어 주어 나타낼수 있음

- 상삼각행렬
    - 주대각선 아래의 모근 원소가 0인 행렬
​
# 상삼각행렬로 변환하는 과정 (가우스 소거법 사용)

가우스 소거법을 사용하여 행렬을 상삼각형으로 변환하는 과정을 자세히 설명하겠습니다. 예시로 3x3 행렬을 사용합니다.

## 예시 행렬 \( A \)

\[
A = \begin{pmatrix}
2 & -1 & -2 \\
-4 & 6 & 3 \\
-4 & -2 & 8
\end{pmatrix}
\]

## 단계별 변환 과정

1. **첫 번째 열의 소거**

첫 번째 행의 첫 번째 원소(피벗)를 이용하여 첫 번째 열의 다른 원소를 0으로 만듭니다.

\[
\text{Pivot} = A[0, 0] = 2
\]

두 번째 행을 처리합니다:

\[
A[1] = A[1] - \left(\frac{A[1, 0]}{A[0, 0]}\right) \cdot A[0]
\]

\[
A[1] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} - \left(\frac{-4}{2}\right) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
\]

\[
A[1] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} + \begin{pmatrix} 4 & -2 & -4 \end{pmatrix} = \begin{pmatrix} 0 & 4 & -1 \end{pmatrix}
\]

세 번째 행을 처리합니다:

\[
A[2] = A[2] - \left(\frac{A[2, 0]}{A[0, 0]}\right) \cdot A[0]
\]

\[
A[2] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} - \left(\frac{-4}{2}\right) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
\]

\[
A[2] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} + \begin{pmatrix} 4 & -2 & -4 \end{pmatrix} = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix}
\]

현재 상태의 행렬 \( A \):

\[
A = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & -4 & 4
\end{pmatrix}
\]

2. **두 번째 열의 소거**

두 번째 행의 두 번째 원소(피벗)를 이용하여 두 번째 열의 아래 원소를 0으로 만듭니다.

\[
\text{Pivot} = A[1, 1] = 4
\]

세 번째 행을 처리합니다:

\[
A[2] = A[2] - \left(\frac{A[2, 1]}{A[1, 1]}\right) \cdot A[1]
\]

\[
A[2] = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix} - \left(\frac{-4}{4}\right) \cdot \begin{pmatrix} 0 & 4 & -1 \end{pmatrix}
\]

\[
A[2] = \begin{pmatrix} 0 & -4 & 4 \end{pmatrix} + \begin{pmatrix} 0 & -4 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 & 5 \end{pmatrix}
\]

현재 상태의 행렬 \( A \):

\[
A = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & 0 & 5
\end{pmatrix}
\]

3. **결과: 상삼각행렬 \( U \)**

변환이 완료된 행렬 \( A \)는 상삼각형 형태의 행렬입니다. 이 행렬은 다음과 같습니다:

\[
U = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & -1 \\
0 & 0 & 5
\end{pmatrix}
\]

# 하삼각행렬로 변환하는 과정 (LU 분해 사용)

하삼각행렬 \( L \)과 상삼각행렬 \( U \)를 동시에 구하는 방법은 LU 분해를 사용하는 것입니다. 이 과정을 예시를 통해 자세히 설명하겠습니다.

## 예시 행렬 \( A \)

\[
A = \begin{pmatrix}
2 & -1 & -2 \\
-4 & 6 & 3 \\
-4 & -2 & 8
\end{pmatrix}
\]

## 단계별 변환 과정 (LU 분해)

1. **첫 번째 열 처리**

첫 번째 열의 피벗을 이용하여 \( U \)의 첫 번째 행을 설정하고, \( L \)의 첫 번째 열을 설정합니다.

\[
U[0, :] = A[0, :] = \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
\]

두 번째 행에 대해:

\[
L[1, 0] = \frac{A[1, 0]}{U[0, 0]} = \frac{-4}{2} = -2
\]

세 번째 행에 대해:

\[
L[2, 0] = \frac{A[2, 0]}{U[0, 0]} = \frac{-4}{2} = -2
\]

2. **두 번째 열 처리**

두 번째 열의 피벗을 이용하여 \( U \)의 두 번째 행을 설정하고, \( L \)의 두 번째 열을 설정합니다.

\[
U[1, :] = A[1, :] - L[1, 0] \cdot U[0, :] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} - (-2) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix}
\]

\[
U[1, :] = \begin{pmatrix} -4 & 6 & 3 \end{pmatrix} + \begin{pmatrix} 4 & -2 & 4 \end{pmatrix} = \begin{pmatrix} 0 & 4 & 7 \end{pmatrix}
\]

세 번째 행에 대해:

\[
L[2, 1] = \frac{A[2, 1] - L[2, 0] \cdot U[0, 1]}{U[1, 1]} = \frac{-2 - (-2) \cdot (-1)}{4} = \frac{-2 - 2}{4} = -1
\]

3. **세 번째 열 처리**

세 번째 열의 피벗을 이용하여 \( U \)의 세 번째 행을 설정하고, \( L \)의 세 번째 열을 설정합니다.

\[
U[2, :] = A[2, :] - L[2, 0] \cdot U[0, :] - L[2, 1] \cdot U[1, :]
\]

\[
U[2, :] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} - (-2) \cdot \begin{pmatrix} 2 & -1 & -2 \end{pmatrix} - (-1) \cdot \begin{pmatrix} 0 & 4 & 7 \end{pmatrix}
\]

\[
U[2, :] = \begin{pmatrix} -4 & -2 & 8 \end{pmatrix} + \begin{pmatrix} 4 & -2 & -4 \end{pmatrix} + \begin{pmatrix} 0 & 4 & 7 \end{pmatrix} = \begin{pmatrix} 0 & 0 & 11 \end{pmatrix}
\]

4. **결과: 하삼각행렬 \( L \)과 상삼각행렬 \( U \)**

\( L \)과 \( U \)는 다음과 같습니다:

\[
L = \begin{pmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
-2 & -1 & 1
\end{pmatrix}
\]

\[
U = \begin{pmatrix}
2 & -1 & -2 \\
0 & 4 & 7 \\
0 & 0 & 11
\end{pmatrix}
\]
