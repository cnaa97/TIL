# 삽입 정렬 \(Insertion Sort\)

* 주어진 데이터를 하나씩 뽑아, 나열된 데이터들이 항상 정렬된 형태를 가지도록, 뽑은 데이터를 바른 위치에 **삽입**해서 나열하는 방식
* 시간복잡도 O\(n²\)

```javascript
function insertionSort (array) {
  let temp, j;
  for (let i=1; i<array.length; i++) {
    temp = array[i]; // 새로운 숫자를 선택함
    for (j = i-1; j >= 0 && temp < array[j]; j--) { 
      // 선택한 숫자를 이미 정렬된 숫자들과 비교하며 넣을 위치를 찾는 과정
      // 선택한 숫자가 정렬된 숫자보다 작으면 한 칸씩 뒤로 밀어낸다
      array[j + 1] = array[j];
    }
    array[j + 1] = temp; // 마지막 빈 칸에 선택한 숫자를 넣어준다.
  }
  return array;
};
insertionSort([5, 6, 1, 2, 4, 3]); // [1, 2, 3, 4, 5, 6]
```

![](https://camo.githubusercontent.com/8f6fedc10da579f13b22b949f6ad29255b6d721f/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f302f30662f496e73657274696f6e2d736f72742d6578616d706c652d33303070782e676966)

![](https://camo.githubusercontent.com/e612023c8a6a653a04bdba1db3a74ae6fb3f894a/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f342f34322f496e73657274696f6e5f736f72742e676966)



