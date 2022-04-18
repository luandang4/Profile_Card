<p align="center">
<a href="#"><img width="80%" height="auto" src="https://codelearn.io/Media/Default/Users/T_5FFlower/blog/git.png"/></a>
</p>

## Git Lecture

### 1.Git Flow

-  **Tổng quan về Git Flow:** Gitflow chỉ là một ý tưởng trừu tượng về quy trình sử dụng Git, Nó chỉ ra cách thức setup các loại branchs khác nhau và cách thức để merge chúng lại với nhau.

-  **Ba trạng thái trong Git:**
<p align="center">
<a href="#"><img width="80%" height="auto" src="https://res.cloudinary.com/practicaldev/image/fetch/s--Si7ksd-d--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/800/1%2AdiRLm1S5hkVoh5qeArND0Q.png
"/></a>
</p>
1. Working directory: Là bản sao một phiên bản của dự án.

2. Staging area (Index): Chứa thông tin về những gì sẽ được commit trong lần commit sắp tới

3. Git directory: Nơi Git lưu trữ các metadata và cơ sở dữ liệu cho dự án của bạn.

-  **Git branch:** Vai trò cụ thể của các branches khác nhau và thời điểm mà chúng cần tương tác.

### 2.Git Clone

**Dùng dể:**

- Copy một Repo từ máy Remote về Local

- Copy một Repo từ thư mục này sang một thư mục khác

- Copy một Repo từ một Url (https) ví dụ GitHub
### Sử dụng git clone
#### Copy Repo từ thư mục này sang thư mục khác
Trên máy của bạn có một Git Repo ở đường dẫn `path-repo`, bạn có thể copy sang vị trí thực mục hiện tại bằng lệnh:
`git clone path-repo`
Có thể chỉ rõ thư mục cần copy về thay vì tại thư mục hiện tại:
`git clone path-repo path-des`
#### Copy Repo từ server về bằng giao thức ssh
Vị dụ Server có kết nối ssh: user@host, trên đó lưu một Repo ở đường dẫn /github.com/username/repo, thì có thể copy về bằng lệnh:
`git clone user@host:/github.com/username/repo.git`
#### Copy Repo bằng giao thức https
Nhiều dịch vụ Git cung cấp kết nối bằng giao thức (https) ví dụ GitHub, GitLab thì copy về bằng lệnh:
`git clone url-repo`
Với `url-repo` là địa chỉ URL ví dụ: https://github.com/Tomosia-LuanDang/Git_Lecture.git
Mặc định nó sẽ sao chép về nhánh hoạt động, để xem tất cả các nhánh có trên Remote dùng lệnh:
`git branch --remote`
Để có thể lấy các nhánh khác nữa bạn cần chạy lệnh `git fetch` và checkout từng nhánh muốn lấy
### 3.Git Checkout

Sử dụng để thay đổi các nhánh làm việc, tạo mới các nhánh làm việc
### Sử dụng git checkout
1. Thay đổi nhánh làm việc: Giả sử đang ở nhánh nào đó, muốn chuyển sang nhánh master thì thực hiện lệnh:
 `git checkout master`
2. Tạo mới 1 nhánh mới: Nếu bạn muốn tạo một nhánh làm việc mới có tên là `branch1` thì sử dụng lệnh:
`git checkout -b branch1`
### 4.Git Add
Sử dụng để đưa các tệp từ vùng Working directory sang vùng Staging, hoặc thự mục cụ thể
### Sử dụng git add
Lệnh `git add` có các cách thực hiện với những tham số khác nhau:
### Đưa vào vùng  **staging**  toàn bộ thư mục làm việc
Trường hợp dùng phổ biến là đưa toàn bộ thư mục làm việc vào giám sát, và tạo snapshot trong vùng staging cho chúng thì dùng cú pháp lệnh:
```
git add --all
Hoặc
git add -A
Hoặc add [thư mục hiên tại]
git add  .
```
### 5.Git Commit
Sử dụng để để đưa các nội dung trong vùng Staging vào CSDL git kèm theo một đoạn nội dung mô tả sự thay đổi của commit này so với commit trước
### Sử dụng git commit
Khi thực hiện thay đổi nội dung tệp trong nhánh đang làm việc và muốn tạo một commit với một message mới sử dụng lệnh:
`git commit -m "Ghi chú về commit"`
Trong trường hợp đã có một commit trước đó ở nhánh hiện tại, nhưng chưa được push lên remote thì ta có thể tạo một commit mới thay thế cho commit cuối cùng đó. Cách này thường được dùng trong trường hợp ta không muốn có quá nhiều commit trong cùng một branch, giúp việc kiểm soát code dễ dàng hơn:
`git commit --amend`
### 6. Git Diff
Sử dụng để hiện thị các thay đổi giữa: thư mục là việc và vùng staging, thư mục làm việc và commit cũ, vùng staging và commit cũ, 2 nhánh, 2 commit,...
### Sử dụng git diff
Mặc định:
`git diff`
Nó hiện thị thông tin tùy ngữ cảnh như sau:
- Thông tin khác nhau giữa thư mục làm việc và commit cuối khi mà vùng Staging không có dữ liệu gì
- Thông tin thay đổi giữa vùng Staging và commit cuối nếu vùng Staging có dữ liệu
### Kiểm tra sự thay đổi thư mục làm việc
Khi có sự thay đổi của thư mục làm việc mà chưa đưa vào vùng Staging, thì có thể xem sự thay đổi của nó với commit cuối
`git diff`
### Kiểm tra sự thay đổi của vùng Staging với commit cuối
`git diff --staged`
### Kiểm tra thay đổi giữa hai commit
`git diff commit1 commit2`
### Kiểm tra sự thay đổi của hai nhánh
`git diff branch1 branch2`
### 7. Git Push
Sử dụng để đẩy các commit mới ở máy trạm (local repo) lên server (remote repo)
### Sử dụng git push
Nếu là lần đầu tiên đẩy Local Repo lên Remote Repo mới khởi tạo thì cần tạo ra một theo dõi kết nối, upstream giữa local và remote, vậy hãy dùng tham số -u. Ví dụ đẩy lên remote có tên origin và tạo upstream cho nhánh master
`git push -u origin master`
Sau khi có upstream, mỗi lần cần đẩy dữ liệu lên remote của nhánh master, chỉ việc thực hiện lệnh
`git push`
Hoặc có thể đẩy một nhánh cụ thể, ví dụ đẩy nhánh branch1 lên remote có tên origin
`git push origin branch1`
### 8. Git Merge
Sử dụng để gộp nhánh, gộp nhánh này vào nhánh khác
Để gộp nhánh branh1 vào nhánh master thì trước tiên cần chuyển không gian làm việc sang nhánh master `git checkout master ` sau đó sử dụng lệnh:
`git merge branch1`
Nếu muốn gộp 1 nhánh bất kỳ nào vào master mà không cần chuyển không gian làm việc thì sử dụng lệnh:
`git merge master branch1`
### 9. Git Rebase
Sử dụng để gộp các commit từ nhánh này vào nhánh khác, bằng cách xây dựng lại các commit base kế thừa từ nhánh cũ và viết lại lịch sử commit sau các commit cơ sở mới. Kỹ thuật này thường được áp dụng để xử lý các conflix trong code
Ví dụ: Muốn gộp các commit của nhánh master vào nhánh branch1, thì đứng ở nhánh branch1 và thực hiện lệnh:
`git rebase master`
Lúc này các commit ở master sẽ được branch kế thừa và đồng thời sẽ xuất hiện các commit này trong log của branch, nếu có sự thay đổi không đồng nhất giữa hai nhánh thì đó là conflix code (xung đột code)

Tài liệu tham khảo:
- https://git-scm.com/book/en/v2
- https://xuanthulab.net/git-va-github/
- https://backlog.com/git-tutorial/vn/intro/intro1_1.html
- https://backlog.com/git-tutorial/vn/intro/intro1_1.html - Tool thực hành git
- https://cbea.ms/git-commit/
