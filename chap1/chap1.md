# CHAP1

## 快速排序算法模板 —— 模板题 AcWing 785. 快速排序

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

## 归并排序算法模板 —— 模板题 AcWing 787. 归并排序

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
## 高精度整数加法

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