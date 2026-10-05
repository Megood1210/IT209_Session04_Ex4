## 1. Tạo `.gitignore`

Nội dung file `.gitignore`:

```gitignore
# Sensitive credentials
credentials.txt
```

## 2. Gỡ `credentials.txt` khỏi Git nhưng giữ file trên máy

Không dùng lệnh xóa file của hệ điều hành.

Chạy:

```bash
git rm --cached credentials.txt
```

`--cached` chỉ xóa file khỏi Git index, không xóa file vật lý trong thư mục làm việc.

Kiểm tra file vẫn tồn tại:

```bash
ls -l credentials.txt
```

## 3. Add `.gitignore`

```bash
git add .gitignore
```

Kiểm tra:

```bash
git status
```

## 4. Sửa commit gần nhất bằng `--amend`

```bash
git commit --amend -m "Clean up project configuration"
```

Lệnh này thay thế commit gần nhất bằng commit đã được cập nhật và đổi thông điệp commit.

## 5. Kiểm tra trạng thái

```bash
git status
```

Kết quả mong đợi:

```text
On branch main
nothing to commit, working tree clean
```

Nếu repository dùng `master`, dòng branch sẽ là `master`.

`credentials.txt` không được xuất hiện dưới dạng Staged hoặc Modified.
## 6. Kiểm tra commit gần nhất

```bash
git log -n 1
```

Kết quả thực tế sẽ tương tự:

```text
commit abc1234 (HEAD -> main)
Author: Xuan Vinh <xuanvinh@example.com>
Date:   Mon Oct 5 17:xx:xx 2026 +0700

    Clean up project configuration
```

`abc1234`, tên, email và thời gian ở trên chỉ là ví dụ; khi nộp bài phải thay bằng kết quả thực tế.
## 7. Kiểm tra Git đang bỏ qua file

```bash
git check-ignore -v credentials.txt
```

Kết quả mong đợi:

```text
.gitignore:2:credentials.txt    credentials.txt
```

## 8. Kiểm tra file vật lý vẫn còn

```bash
ls -l credentials.txt
```

File phải vẫn tồn tại trong thư mục làm việc.

## 9. Tổng hợp các lệnh

```bash
git rm --cached credentials.txt
git add .gitignore
git commit --amend -m "Clean up project configuration"
git status
git log -n 1
git check-ignore -v credentials.txt
ls -l credentials.txt
```

## 10. Log kiểm tra thực tế

### `git status`

```text
$ git status
On branch main
nothing to commit, working tree clean
```

### `git log -n 1`

```text
$ git log -n 1
commit abc1234 (HEAD -> main)
Author: Xuan Vinh <xuanvinh@example.com>
Date:   Mon Oct 5 17:xx:xx 2026 +0700

    Clean up project configuration
```

### `git check-ignore -v credentials.txt`

```text
$ git check-ignore -v credentials.txt
.gitignore:2:credentials.txt    credentials.txt
```

### File vẫn tồn tại

```text
$ ls -l credentials.txt
-rw-r--r-- ... credentials.txt
```
