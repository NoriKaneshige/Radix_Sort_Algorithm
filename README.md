# Radix_Sort_Algorithm

![radix_sort_visual](radix_sort_visual.gif)

![radix_sort_1](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_1.png)
![radix_sort_2](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_2.png)
![radix_sort_3](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_3.png)
![radix_sort_4](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_4.png)
![radix_sort_5](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_5.png)
![radix_sort_6](https://github.com/NoriKaneshige/Quick_Sort_Algorithm/blob/master/radix_sort_6.png)


> ## Radix_Sort Helper Method: :wink:

``` js
function getDigit(num, i) {
  return Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;
}

function digitCount(num) {
  if (num === 0) return 1;
  return Math.floor(Math.log10(Math.abs(num))) + 1;
}

function mostDigits(nums) {
  let maxDigits = 0;
  for (let i = 0; i < nums.length; i++) {
    maxDigits = Math.max(maxDigits, digitCount(nums[i]));
  }
  return maxDigits;
}

console.log(mostDigits([23,567,89,12234324,90])) // 8
```

> ## Radix_Sort: :laughing:

``` js
function radixSort(nums){
    let maxDigitCount = mostDigits(nums);
    for(let k = 0; k < maxDigitCount; k++){
        let digitBuckets = Array.from({length: 10}, () => []);
        for(let i = 0; i < nums.length; i++){
            let digit = getDigit(nums[i],k);
            digitBuckets[digit].push(nums[i]);
        }
        nums = [].concat(...digitBuckets);
    }
    return nums;
}

console.log(radixSort([23,345,5467,12,2345,9852])) // [ 12, 23, 345, 2345, 5467, 9852 ]
```
