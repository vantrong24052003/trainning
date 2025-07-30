# Hướng dẫn Git cơ bản cho Intern

## PHẦN 1: CẤU HÌNH GIT LẦN ĐẦU

**Bước 1: Thiết lập thông tin cá nhân**
```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email@example.com"
```

Ví dụ:
```bash
git config --global user.name "Du Thanh Duoc"
git config --global user.email "duthanhduoc@gmail.com"
```

**Bước 2: Kiểm tra cấu hình đã đúng chưa**
```bash
git config --list
git config user.name
git config user.email
```

## PHẦN 2: TẠO SSH KEY ĐỂ KẾT NỐI GITHUB

**Bước 1: Tạo SSH key mới**
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**Bước 2: Nhập thông tin khi được hỏi**
- Đường dẫn lưu file: Nhấn Enter để dùng mặc định
- Passphrase: Nhấn Enter để bỏ trống (khuyên dùng cho intern)

**Bước 3: Xem nội dung public key để copy lên GitHub**
```bash
cat ~/.ssh/id_ed25519.pub
```

Trên Windows:
```bash
cat /c/Users/username/.ssh/id_ed25519.pub
```

**Bước 4: Copy key này và paste vào GitHub Settings > SSH Keys**

## PHẦN 3: CÁC LỆNH GIT CƠ BẢN PHẢI BIẾT

### Khởi tạo và Clone project

**Khởi tạo Git trong thư mục hiện tại:**
```bash
git init
```

**Clone project có sẵn từ GitHub:**
```bash
git clone https://github.com/username/repository.git
```

### Kiểm tra trạng thái project

**Xem file nào đã thay đổi:**
```bash
git status
```

**Xem lịch sử commit:**
```bash
git log
git log --oneline
```

### Thêm file vào Git (Staging)

**Thêm 1 file cụ thể:**
```bash
git add filename.txt
```

**Thêm tất cả file đã thay đổi (dùng nhiều nhất):**
```bash
git add .
```

**Thêm file theo loại:**
```bash
git add *.js
git add *.css
```

### Lưu thay đổi (Commit)

**Commit với message mô tả:**
```bash
git commit -m "Mô tả thay đổi ngắn gọn"
```

**Commit nhanh (add + commit cùng lúc):**
```bash
git commit -am "Mô tả thay đổi"
```

**Ví dụ message commit tốt:**
```bash
git commit -m "Thêm tính năng đăng nhập"
git commit -m "Sửa lỗi hiển thị menu"
git commit -m "Cập nhật style cho header"
```

### Đồng bộ với GitHub (Push/Pull)

**Kéo code mới nhất từ GitHub về:**
```bash
git pull
```

**Đẩy code lên GitHub:**
```bash
git push
```

**Lần đầu push project lên GitHub:**
```bash
git push -u origin main
```

**Xem remote repository:**
```bash
git remote -v
```

## PHẦN 4: QUY TRÌNH LÀM VIỆC HÀNG NGÀY

**Bước 1: Mở project và pull code mới nhất**
```bash
git pull
```

**Bước 2: Code tính năng của bạn**
- Viết code, sửa file...

**Bước 3: Kiểm tra những gì đã thay đổi**
```bash
git status
```

**Bước 4: Thêm file đã thay đổi**
```bash
git add .
```

**Bước 5: Commit với message rõ ràng**
```bash
git commit -m "Mô tả ngắn gọn những gì đã làm"
```

**Bước 6: Push lên GitHub**
```bash
git push
```

## PHẦN 5: LÀM VIỆC VỚI BRANCH

### Tại sao cần Branch?
- Branch giúp phát triển tính năng mới mà không ảnh hưởng code chính
- Nhiều người có thể làm việc song song
- Dễ dàng test và review code

### Các lệnh Branch cơ bản

**Xem branch hiện tại:**
```bash
git branch
```

**Tạo branch mới:**
```bash
git branch feature-login
```

**Chuyển sang branch khác:**
```bash
git checkout feature-login
```

**Tạo và chuyển sang branch mới (gộp 2 lệnh trên):**
```bash
git checkout -b feature-login
```

**Merge branch vào main:**
```bash
git checkout main
git merge feature-login
```

**Xóa branch không cần:**
```bash
git branch -d feature-login
```

## PHẦN 6: XỬ LÝ TÌNH HUỐNG THƯỜNG GẶP

### Khi có Conflict (xung đột code)

**Bước 1: Pull code về**
```bash
git pull
```

**Bước 2: Mở file conflict, tìm những dòng có:**
```
Other changes
```

**Bước 3: Xóa các ký hiệu <, =, > và giữ lại code đúng**

**Bước 4: Add và commit**
```bash
git add .
git commit -m "Resolve conflict"
git push
```

### Hoàn tác thay đổi

**Hủy thay đổi file chưa add:**
```bash
git checkout -- filename.txt
```

**Hủy add file:**
```bash
git reset HEAD filename.txt
```

**Xem thay đổi trước khi commit:**
```bash
git diff
```

### Lưu tạm thay đổi (Stash)

**Lưu tạm khi cần chuyển branch gấp:**
```bash
git stash
```

**Lấy lại thay đổi đã lưu tạm:**
```bash
git stash pop
```

## PHẦN 7: FILE .GITIGNORE

Tạo file `.gitignore` trong thư mục gốc project để loại trừ file không cần:

```
node_modules/
.env
.vscode/
.idea/
dist/
build/
*.log
.DS_Store
```

## PHẦN 8: CÁC MẸO HỮU ÍCH CHO INTERN

### Alias để gõ lệnh nhanh hơn
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```

Sau khi tạo alias, có thể gõ:
```bash
git st      # thay vì git status
git co main # thay vì git checkout main
git br      # thay vì git branch
git ci -m "message" # thay vì git commit -m "message"
```

### Xem lịch sử commit đẹp
```bash
git log --oneline --graph --decorate
```

## PHẦN 9: NHỮNG LỖI THƯỜNG GẶP VÀ CÁCH FIX

**Lỗi: "Please commit your changes or stash them"**
```bash
git add .
git commit -m "Save current work"
git pull
```

**Lỗi: "Permission denied (publickey)"**
- Kiểm tra SSH key đã add vào GitHub chưa
- Kiểm tra SSH agent: `ssh-add ~/.ssh/id_ed25519`

**Lỗi: Push bị reject**
```bash
git pull
# Giải quyết conflict nếu có
git push
```

## PHẦN 10: NGUYÊN TẮC LÀM VIỆC CHO INTERN

### DO (Nên làm)
- Luôn pull trước khi bắt đầu code
- Commit thường xuyên với message rõ ràng
- Tạo branch cho tính năng mới
- Test code trước khi push
- Hỏi senior khi không chắc chắn

### DON'T (Không nên làm)
- Không commit file nhạy cảm (.env, password)
- Không force push trừ khi được cho phép
- Không commit code chưa test
- Không viết commit message mơ hồ kiểu "fix bug"
- Không xóa branch main hoặc branch quan trọng

### Message commit tốt vs xấu

**Tốt:**
```bash
git commit -m "Thêm API đăng nhập người dùng"
git commit -m "Sửa lỗi validation form contact"
git commit -m "Cập nhật responsive cho mobile"
```

**Xấu:**
```bash
git commit -m "update"
git commit -m "fix bug"
git commit -m "done"
```

## PHẦN 11: TÀI NGUYÊN HỌC THÊM

- **Git Documentation**: https://git-scm.com/doc
- **GitHub Guides**: https://guides.github.com/
- **Interactive Tutorial**: https://learngitbranching.js.org/
- **Git Cheat Sheet**: https://training.github.com/

**Lưu ý cuối:** Đây là những lệnh cơ bản nhất mà intern cần biết. Hãy thực hành thường xuyên và đừng ngại hỏi senior khi gặp khó khăn!
