# 5 Sorting Algorithms

a = [10,3,4,1,66,32,12,33,54]

# Bubble Sort

```
  def bubble_sort(array)
    n = array.length
    loop do
      swapped = false

      (n-1).times do |i|
        if array[i] > array[i+1]
          array[i], array[i+1] = array[i+1], array[i]
          swapped = true
        end
      end
      break if not swapped
    end

    array
  end
```

print bubble_sort(a)

# Merge Sort

```
def mergesort(array)
  
  def merge(left_sorted, right_sorted)
    res = []
    l = 0
    r = 0

    loop do
      break if r >= right_sorted.length and l >= left_sorted.length

      if r >= right_sorted.length or (l < left_sorted.length and left_sorted[l] < right_sorted[r])
        res << left_sorted[l]
        l += 1
      else
        res << right_sorted[r]
        r += 1
      end
    end

    return res
  end

  def mergesort_iter(array_sliced)
    return array_sliced if array_sliced.length <= 1

    mid = array_sliced.length/2 - 1
    left_sorted = mergesort_iter(array_sliced[0..mid])
    right_sorted = mergesort_iter(array_sliced[mid+1..-1])
    return merge(left_sorted, right_sorted)
  end

  mergesort_iter(array)
end
```

print mergesort(a)

# Selection Sort 

```
def selection_sort(list)  
  (0...list.length).each do |i|
    k = i

    (i+1...list.length).each do |j|
      k = j if list[j] < list[k]
    end
    if k != i
      list[i],list[k] = list[k],list[i] 
    end
  end
  list
end 
```

print selection_sort(a)

# Insertion Sort

```
def insertion_sort(list)  
  (1...list.length).each do |i| 
      k = i
      while k > 0 && list[k] < list[k-1]
        list[k], list[k-1] = list[k-1], list[k]
        k -= 1
      end
  end
  list
end 
```

print insertion_sort(a)

# Quick Sort

```
def quick_sort(array)
  return array if array.length <= 1
  pivot = array.delete_at(rand(array.length))

  left = Array.new
  right = Array.new
  
  array.each do |x|
    if x <= pivot
      left << x
    else
      right << x
    end
  end

  return *quick_sort(left), pivot ,*quick_sort(right)
end
```

print quick_sort(a)

