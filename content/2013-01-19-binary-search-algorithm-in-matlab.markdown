layout: post
title: Binary Search Algorithm in MATLAB
date: 2011-01-19 06:40
comments: true
categories: matlab

Here’s how I did a quick binary search in MATLAB:

```matlab
    randNum = rand();

    minIndex = 2;

    maxIndex = length(cdf_scatterSM);

    midIndex = minIndex + round((maxIndex - minIndex)/2);

    while randNum ~= cdf_scatterSM(midIndex) && maxIndex >= minIndex

        midIndex = minIndex + round((maxIndex - minIndex)/2);

        if randNum > cdf_scatterSM(midIndex)

            minIndex = midIndex + 1;

        elseif randNum < cdf_scatterSM(midIndex)

            maxIndex = midIndex - 1;

        end

    end

    midIndex = minIndex + round((maxIndex - minIndex)/2);

    k = midIndex;
```

Note: The index was then used for linear interpolation, hence the ‘minIndex’ value starting at 2 instead of 1 (remember, MATLAB indexes from 1).

**Edit 5/31/11:** I just discovered a bug in this algorithm (I changed it above). The while loop 2nd condition should be “maxIndex >= minIndex”. Apologies.