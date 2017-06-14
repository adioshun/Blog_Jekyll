[선형대수학 강좌](https://www.youtube.com/playlist?list=PLSN_PltQeOyjDGSghAf92VhdMBeaLZWR3): 이상화 교수, [[교재]](http://www.kocw.net/home/search/kemView.do?kemId=977757)


#
선형성 정의

행렬 연산을 하려면 선형성을 만족 해야 함.

선형성 요구 사항
- Superposition : $$f(x_1 + x_2) = f(x_1) + f(x_2) $$

- Homogeniety : $$ f(ax) = a f(x) $$

> 합쳐서 $$ f(a_1 x_1 + a_2 x_2) = a_1 f(x_1) + a_2 f(x_2) $$

`원점을 지나는 평면상의 직선은 선형성을 만족 하며, 백터라고 부름`

# 1차 연립 방법식과 가우스 소거법

Singular case
- 답이 없음
- 답이 무수히 많음

1. row form
- 평행한 경우 (닶이 없음)
- 겹침 (답이 무수히 많음)

2. Column form
-

## 가우스 소거법
- 연립 방정식을 푸는 방법
- 미지수의 갯수와 방정식의 갯수가 같은 경우

`All pivots are non-zero -> G.E has a unique solution`

Matrix로 표현 = upper Triangular U

## Breakdown
- pivot에 `0`이 존재 하여 가우스 소거법을 사용 못할경우, 순서를 바꾸어 문제 해결 --> pivoting 

## 1.4 Matrix Multiplication


#
3강 LU 분할

## 1.5 Triangular Factors

$$ A x = b $$

$$ A = LU $$

Lower Triangular matrix * Upper Triangular matrix

> ? 가우시안 소거법을 행렬로 표현 -> Elementary Matrix $$ E_{31}E_{21} A $$ => U (upper triangular matrix)

###### Elementary Matrix in GE
$$
E_{21} = \begin{bmatrix}1 & 0 & 0 \\-l_{21} & ? & ? \\0 & 0 & 1 \end{bmatrix}
$$

해석 : 2번식 - (1번식 * $$L_{21}$$)



[참고]
$$
E_{21}^{-1} = \begin{bmatrix}1 & 0 & 0 \\l_{21} & 1 & 0 \\0 & 0 & 1 \end{bmatrix}

$$

$$ E_{21}E_{21}^{-1} = I $$

---

#### LU는

$$
E_{32}E_{31}E_{21}A = U
$$
$$
A = E_{32}^{-1}E_{31}^{-1}E_{21}^{-1} U
$$
$$
\begin{bmatrix}1 & 0 & 0 \\l_{21} & 1 & 0 \\0 & 0 & 1 \end{bmatrix}

\begin{bmatrix}1 & 0 & 0 \\0 & 1 & 0 \\l_{31} & 0 & 1 \end{bmatrix}

\begin{bmatrix}1 & 0 & 0 \\0 & 1 & 0 \\0 & l_{32} & 1 \end{bmatrix} U
$$
$$
\begin{bmatrix}1 & 0 & 0 \\l_{21} & 1 & 0 \\l_{31} & l_{32} & 1 \end{bmatrix}
= Lower Triangular matrix = L
$$

---
### LU 예시

$$
A = \begin{bmatrix} 1 & 2 \\ 3 & 8 \end{bmatrix}
$$

2번식 - (3번식) x 1

$$
U = \begin{bmatrix} 1 & 2 \\ 0 & 2 \end{bmatrix}
$$

$$
L = \begin{bmatrix} 1 & 0 \\ 3 & 1 \end{bmatrix}
$$




> ? Diagonal matrix(D) = A = LU = LDU


# Permutation matrix(p)
- Pivoting = Row Exchange을 행렬로 표시

- has the same rows with Identity Matrix
- There is a single '1' in every rows and column


- $$P_{21} $$ = 2번행렬와 1번 행렬을 서로 바꿈
$$
\begin{bmatrix}0 & 1 & 0 \\1 & 0 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

$$P^{-1} = P^{T} $$ :P의 역행렬은 Transform하면 된다.


#
# 1.6 Inverse & Transpose

### A. Inverse(역행렬)

$$ AA^{-1} = A^{-1}A = I $$

역행렬 존재 요구 사항
- 만약, 가우스 소거법 결과과 N 개의 피폿을 생성할때 (=가우스 소거법이 가능하다)
- The inverse is unique
- if $$ A^{-1} $$ exists, Ax = b => $$AA^{-1}x = A^{-1}b $$
- Assume that there is a non-zero vector X such that Ax = 0 (b=0) ==> then $$ A^{-1} $$ does not exist 
- 2x2일때의 역행렬은 공식으로 유도 된다. (3x3 이상일때는 가우시안 조르단 방식을 이용)
- Diagonal Matrix의 역행렬은 $$ d_n -> 1/d_n $$
- 대각선은 0이 존재 하면 안된다. (곱해서 0이 되면 안됨)
- The inverse comes in the reverse order
- $$ (ABC)^{-1} = C^{-1}B^{-1}A^{-1} $$

###### $$A^{-1}$$ Gauss-Jordan Method

### B. Transpose (전치행렬)
$$ A^T = a_{ij} -> a_{ji} $$

$$ (A+B)^T = A^T + B^T$$

$$ (AB)^T = B^TA^T$$

$$(A^{-1})^T = (A^T)^{-1} $$



###### Symmetric Matrix (대칭행렬)
$$ A^T = A $$ : 전치해도 값이 같다.

- if A is symmetrix and invertible, then $$ A^{-1}$$ is too



























