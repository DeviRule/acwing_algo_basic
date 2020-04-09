# CHAP1

## 排序
### 快速排序算法模板 —— 模板题 AcWing 785. 快速排序

```C++
    void quick_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while (i < j)
    {
        do i ++ ; while (q[i] < x);
        do j -- ; while (q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }
    quick_sort(q, l, j), quick_sort(q, j + 1, r);
}

```

### 归并排序算法模板 —— 模板题 AcWing 787. 归并排序

```C++

    void merge_sort(int q[], int l, int r)
{
    if (l >= r) return;

    int mid = l + r >> 1;
    merge_sort(q, l, mid);
    merge_sort(q, mid + 1, r);

    int k = 0, i = l, j = mid + 1;
    while (i <= mid && j <= r)
        if (q[i] < q[j]) tmp[k ++ ] = q[i ++ ];
        else tmp[k ++ ] = q[j ++ ];

    while (i <= mid) tmp[k ++ ] = q[i ++ ];
    while (j <= r) tmp[k ++ ] = q[j ++ ];

    for (i = l, j = 0; i <= r; i ++, j ++ ) q[i] = tmp[j];
}

```

## 二分

### 整数二分

### 浮点二分

## 高精度

### 高精度整数加法

```C++
vector<int> add(vector<int> &a, vector<int> &b)
{
    vector<int> c;
    int t = 0;
    for(int i = 0; i  < a.size() || i < b.size(); i++)
    {
        if(i < a.size()) t += a[i];
        if(i < b.size()) t += b[i];
        c.push_back(t % 10);
        t /= 10;
    }
    if (t > 0) c.push_back(1);
    return c;
}

```

### 高精度减法

保证A >  B

### 一维前缀和

各个前缀和的值
S<sub>i</sub> = S<sub>i-1</sub> + a<sub>i</sub>
注意 S<sub>0</sub> = 0
区间取值
value between S<sub>l</sub>  and S<sub>r</sub> = S<sub>r</sub> - S<sub>l-1</sub>

### 二维前缀和

S[i, j] = 第i行j列格子左上部分所有元素的和
以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵的和为：
S[x2, y2] - S[x1 - 1, y2] - S[x2, y1 - 1] + S[x1 - 1, y1 - 1]

### 差分

b[] 为 a[] 差分
b[ i ] = a[ i ] - a[ i-1 ]
使得 a[] 为b[] 前缀和
a[ i ] = b[ i ] + b[ i-1 ]
给区间[l, r]中的每个数加上c：B[ l ] += c, B[r + 1] -= c

### 差分矩阵

给以(x1, y1)为左上角，(x2, y2)为右下角的子矩阵中的所有元素加上c：
S[x1, y1] += c, S[x2 + 1, y1] -= c, S[x1, y2 + 1] -= c, S[x2 + 1, y2 + 1] += c