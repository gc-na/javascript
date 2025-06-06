# [লিনাক্স] C Shell (csh) sort ব্যবহার: তথ্য সাজানো

## Overview
`sort` কমান্ডটি একটি ফাইল বা ইনপুটের লাইনগুলোকে সাজানোর জন্য ব্যবহৃত হয়। এটি সাধারণত টেক্সট ফাইলের লাইনগুলোকে অ্যালফাবেটিক্যাল বা সংখ্যাগতভাবে সাজাতে সাহায্য করে।

## Usage
`sort` কমান্ডের মৌলিক সিনট্যাক্স হলো:

```
sort [options] [arguments]
```

## Common Options
- `-r`: ফলাফলকে বিপরীত ক্রমে সাজায়।
- `-n`: সংখ্যাগতভাবে সাজানোর জন্য ব্যবহৃত হয়।
- `-k`: নির্দিষ্ট কলাম অনুযায়ী সাজানোর জন্য।
- `-u`: ইউনিক লাইনগুলোকে রাখে, ডুপ্লিকেটগুলো বাদ দেয়।

## Common Examples
- একটি ফাইলের লাইনগুলো অ্যালফাবেটিক্যালভাবে সাজানো:
  ```csh
  sort filename.txt
  ```

- একটি ফাইলের লাইনগুলো বিপরীত ক্রমে সাজানো:
  ```csh
  sort -r filename.txt
  ```

- সংখ্যাগতভাবে সাজানো:
  ```csh
  sort -n numbers.txt
  ```

- নির্দিষ্ট কলাম অনুযায়ী সাজানো (যেমন দ্বিতীয় কলাম):
  ```csh
  sort -k 2 filename.txt
  ```

- ইউনিক লাইনগুলোকে বের করা:
  ```csh
  sort -u filename.txt
  ```

## Tips
- ফাইলের আকার বড় হলে, `-o` অপশন ব্যবহার করে সাজানো ফলাফল একটি নতুন ফাইলে সংরক্ষণ করতে পারেন।
- যদি আপনি একটি পাইপের মাধ্যমে ইনপুট দিতে চান, তাহলে `sort` কমান্ডটি অন্য কমান্ডের সাথে সংযুক্ত করতে পারেন।
- সাজানোর আগে ফাইলের কনটেন্ট চেক করতে `cat` কমান্ড ব্যবহার করুন, যাতে আপনি নিশ্চিত হতে পারেন যে সঠিক তথ্য সাজানো হচ্ছে।