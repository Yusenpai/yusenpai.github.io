---
layout: post
title: "Mark down Cơ bản"
subtitle: ""
date: 2025-01-15
author: "yusenpai"
header-img: "img/post-bg-2015.jpg"
tags: []
---

# Markdown cơ bản

Markdown là ngôn ngữ trình bày đơn giản và tiện lợi để trình bày văn bản. Mỗi file markdown có đuôi `.md` hoặc `.markdown`. Visual Code hỗ trợ viết và xem file markdown. Bấm Ctrl + Shift + V để mở preview cho file markdown hiện tại.

# Tiêu đề và đề mục

Để tạo tiêu đề hoặc đề mục, thêm dấu "#" đứng trước từ hoặc câu. Bao nhiêu dấu "#" thì cấp đề mục bấy nhiêu. Ví dụ:

```html
# Đề mục cấp 1
## Đề mục cấp 2
### Đề mục cấp 3
#### Đề mục cấp 4
```

# Đề mục cấp 1
## Đề mục cấp 2
### Đề mục cấp 3
#### Đề mục cấp 4
...

Lưu ý:

| ✅ Nên     | ❌ Không nên |
| --------- | ----------- |
| # Tiêu đề | #Tiêu đề    |

| ✅ Nên| ❌ Không nên |
|-|-|
| Nhớ cách dòng trước... <br> <br> # Tiêu đề <br> <br> ... và cách dòng sau tiêu đề | Nếu không cách dòng, hiển thị sẽ sai.<br># Tiêu đề<br>Đừng làm z =)) |

# Đoạn văn

Để viết một đoạn văn, dùng cách dòng giữa mỗi đoạn.

Ví dụ thế này:

```html
Tôi thích dùng markdown.

Tôi sẽ viết đoạn văn như thế này và sau đó cũng vậy.
```
Lưu ý:

| ✅ Nên     | ❌ Không nên |
| --------- | ----------- |
| Đừng thêm tabs hoặc dấu cách trước câu.<br> <br>Giữ mỗi đoạn thẳng hàng nhau thế này |	         Thêm tabs hoặc dấu cách có thể gây lỗi hiển thị |

# Nhấn mạnh

```html
Có thể nhấn mạnh bằng cách **tô đậm**, *in nghiêng* hoặc ~~gạch ngang~~.

Phím tắt: Bôi đen rồi nhấn...
- Ctrl + B để **tô đậm**
- Ctrl + I để *in nghiêng*
- Ctrl + I, B để ***bôi đậm và in nghiêng***
```

# Khối trích dẫn

```html

> Thêm dấu ">" ở đầu câu
> 
> Một khối trích dẫn có thể chứa nhiều đoạn văn. Thêm ">" đầu mỗi đoạn.

> Khối trích dẫn có thể lồng nhau. Như thế này:
> > Khối trích dẫn trong khối trích dẫn

> Có thể thêm các thành phần khác vào khối trích dẫn. Như thế này:
>
> #### Buổi sáng mai
>
> - Đánh răng
> - Rửa mặt
>
> *Mọi thứ* đều theo đúng **kế hoạch**.

```

> Thêm dấu ">" ở đầu câu
> 
> Một khối trích dẫn có thể chứa nhiều đoạn văn. Thêm ">" đầu mỗi đoạn.

> Khối trích dẫn có thể lồng nhau. Như thế này:
> > Khối trích dẫn trong khối trích dẫn

> Có thể thêm các thành phần khác vào khối trích dẫn. Như thế này:
>
> #### Buổi sáng mai
>
> - Đánh răng
> - Rửa mặt
>
> *Mọi thứ* đều theo đúng **kế hoạch**.

Nhớ thêm cách dòng ở trước và sau khối trích dẫn.

# Danh sách

## Danh sách có thứ tự

```html
1. Thành phần 1
2. Thành phần 2
3. Thành phần 3
```

1. Thành phần 1
2. Thành phần 2
3. Thành phần 3

Hoặc thế này:

```html
1. Markdown
2. Chả quan tâm
1. Bạn đánh số thế nào
2. Cuối cùng vẫn hiện đúng thứ tự.
```

1. Markdown
2. Chả quan tâm
1. Bạn đánh số thế nào
2. Cuối cùng vẫn hiện đúng thứ tự.

Hoặc thế này:

```html
1. Thành phần 1
2. Thành phần 2
   1. Bấm Tab để thụt dòng thành phần 2.1
   2. Thành phần 2.2
3. Thành phần 3
```

1. Thành phần 1
2. Thành phần 2
   1. Bấm Tab để thụt dòng thành phần 2.1
   2. Thành phần 2.2
3. Thành phần 3


Lưu ý:

| ✅ Nên     | ❌ Không nên |
| --------- | ----------- |
| 1. Thành phần 1 | 1) Thành phần 1 |
| 2. Thành phần 2 | 2) Thành phần 2|

## Danh sách không thứ tự

- Đây là danh sách không thứ tự
- Thêm dấu "-" trước câu
- Thế là xong.
  - Hoặc thêm tabs
  - Để thụt vô thế này
	- Hoặc thế này

## Thêm thành phần khác vào danh sách

- Đây là dòng đầu tiên của danh sách
- Đây là dòng thứ hai của danh sách

	Còn đây là đoạn văn ở giữa danh sách. Thêm tab đầu đoạn văn.

- Đây là dòng thứ ba của danh sách
	
	> Còn đây là khối trích dẫn

- Và đây là dòng cuối cùng.

# Khối code

```c++
// Đây là khối code nè. Nhớ thêm chữ c++ để bôi màu cho code nhé

void main(){
	printf("Hello World\n");
	return 0;
}
```

```python
# Còn cái này là code python
import numpy as np
print("hello world")
```

Còn cái này là khối code 1 dòng `uint8_t a = 10;`

# Đường kẻ ngang

Thêm đường kẻ ngang thế này:

***

hoặc 

---

# Link

Thêm link như thế này: [Đây là link tới Google](https://www.google.com)

Thêm tựa đề cho link thế này (để con chuột lên một lúc sẽ thấy):

[Youtube](https://www.youtube.com/watch?v=dQw4w9WgXcQ "Tốt hơn tiktok")

Hoặc thêm link nhanh thì: <https://www.youtube.com/watch?v=dQw4w9WgXcQ>

# Ảnh

Thêm ảnh nè:

![Đây là chữ hiện lên nếu ảnh lỗi](https://mdg.imgix.net/assets/images/san-juan-mountains.jpg?auto=format&fit=clip&q=40&w=1080)

hoặc dùng đường dẫn thư mục cũng được:

![Đây là chữ hiện lên nếu ảnh lỗi](images/images.jpeg)

Kéo ảnh vào Visual Code, nhấn giữ Shift rồi thả chuột để thêm ảnh nhanh.

# Bảng

| Cột 1     | Cột 2 |
| --------- | ----- |
| Header    | Title |
| Paragraph | Text  |

| Cột 1     | Cột 2 |
| - | - |
| Thế này| Title |
| Cũng được | Text  |

# Danh sách công việc

- [x] Học viết Markdown
- [ ] Làm bài tập
- [ ] Nộp bài chấm điểm

# Emoji

😂🤡😃🙃

# Mục lục

Cái này phải cài *Extension:Markdown All in One* trên Visual Code. Rồi bấm Ctrl + Shift + P, tìm *Markdown All in One: Create Table of Contents* thì nó ra này:

- [Markdown cơ bản](#markdown-cơ-bản)
- [Tiêu đề và đề mục](#tiêu-đề-và-đề-mục)
- [Đề mục cấp 1](#đề-mục-cấp-1)
	- [Đề mục cấp 2](#đề-mục-cấp-2)
		- [Đề mục cấp 3](#đề-mục-cấp-3)
			- [Đề mục cấp 4](#đề-mục-cấp-4)
- [Đoạn văn](#đoạn-văn)
- [Nhấn mạnh](#nhấn-mạnh)
- [Khối trích dẫn](#khối-trích-dẫn)
- [Danh sách](#danh-sách)
	- [Danh sách có thứ tự](#danh-sách-có-thứ-tự)
	- [Danh sách không thứ tự](#danh-sách-không-thứ-tự)
	- [Thêm thành phần khác vào danh sách](#thêm-thành-phần-khác-vào-danh-sách)
- [Khối code](#khối-code)
- [Đường kẻ ngang](#đường-kẻ-ngang)
- [Link](#link)
- [Ảnh](#ảnh)
- [Bảng](#bảng)
- [Danh sách công việc](#danh-sách-công-việc)
- [Emoji](#emoji)
- [Mục lục](#mục-lục)


