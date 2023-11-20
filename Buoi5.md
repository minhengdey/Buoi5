## I. Version Control là gì và tại sao cần dùng nó?

### 1. Version Control là gì?

**_Hệ thống quản lý phiên bản (Version Control Systems - VCS)_** là các công cụ để theo dõi những thay đổi trong mã nguồn (hay các thư mục và tập tin). Đúng như tên gọi của chúng, các công cụ này giúp ta lưu giữ lịch sử thay đổi và thậm chí là tạo điều kiện cho việc hợp tác với người khác. Trong phạm vi tệp, VCS quản lý thay đổi (thêm, sửa, xóa) chi tiết từng dòng. Hiện nay, các VCS phổ biến bao gồm Git, Mercurial, SVN và Preforce.

### 2. Tại sao ta cần dùng VCS?

Tác dụng chính của VCS :

- Lưu lại lịch sử các version của bất kỳ thay đổi nào của dự án. Giúp xem lại các sự thay đổi hoặc khôi phục (revert) lại sau này.

- Việc chia sẻ code trở nên dễ dàng hơn, các lập trình viên có thể chia sẻ public cho bất kỳ ai, hoặc private chỉ cho một số người có thẩm quyền để truy cập vào và lấy code về.

## II. Các khái niệm về Git: Local Repository, Remote Repository, Branch, Commit, Merge, Pull, Push, Clone, Fork.

**_Git_** là một hệ thống quản lý phiên bản phân tán (Distributed Version Control System – DVCS), nó là một trong những hệ thống quản lý phiên bản phân tán phổ biến nhất hiện nay. Git cung cấp cho mỗi lập trình viên kho lưu trữ (repository) riêng chứa toàn bộ lịch sử thay đổi.

### 1. Repository.

**_Repository_** là nơi lưu trữ tất cả những thông tin cần thiết để duy trì và quản lý các sửa đổi và lịch sử của dự án (nơi trữ source code và các thay đổi trên đống source code này).

Có 2 loại repository:

- **_Local Repository:_** là repository nằm trên chính máy tính của chúng ta, repository này sẽ đồng bộ hóa với remote repository bằng các lệnh của git.

- **_Remote Repository:_** là repository được cài đặt trên server chuyên dụng. Ví dụ: GitHub, GitLab, Bitbucket,...

![Alt text](image.png)

### 2. Branch.

**_Branch_** là cái dùng để phân nhánh và ghi lại luồng của lịch sử. Branch đã phân nhánh sẽ không ảnh hưởng đến branch khác nên có thể tiến hành nhiều thay đổi đồng thời trong cùng 1 repository

Khi tạo mới một repository thì nhánh mặc định sẽ "master". Nhánh master thông thường là nhánh chính của ứng dụng.

Cú pháp tạo 1 branch `alpha`:

> $ git branch alpha

### 3. Commit.

Là thao tác để lưu lại trạng thái hiện tại trên hệ thống, ghi nhận lại lịch sử các xử lý: thêm, xóa, cập nhật các file hay thư mục trên repository.

Khi thực hiện, repository sẽ ghi lại sự khác biệt giữa lần commit trước so với hiện tại. Chúng được ghi nối tiếp nhau theo thứ tự thời gian. Do đó, bạn có thể xem lại lịch sử thay đổi trong quá khứ dựa theo các commit trước đó.

![Alt text](image-1.png)

### 4. Merge.

Là việc hợp nhất một nhánh phát triển hoặc hợp nhất lịch sử thay đổi vào nhánh khác.

_Ví dụ:_ bạn phát triển xong 1 tính năng, đã test/kiểm tra các kiểu và thấy nó hoàn chỉnh, có thể tích hợp vào phần mềm thì bạn sẽ tiến hành merge code. Dĩ nhiên trong thực tế thì bạn đôi khi cần phải mất một vài thao tác khác như commit, push,... để có thể merge được code.

Cú pháp:

> $ git merge <branch_name>

hoặc

> $ git merge <branch-name> <merged-branch-name>

### 5. Pull.

Là hành động cập nhật các thay đổi từ remote repo xuống local repo. Hiểu một cách đơn giản, **_Pull_** là việc lập trình viên đề xuất các thay đổi mới cho Master Branch. Đây là tính năng phù hợp với các dự án cần làm việc nhóm. Người thực hiện có thể dùng tính năng Pull Request để yêu cầu người có nhiệm vụ thực hiện bảo trì kho lưu trữ để xem xét các thay đổi của hệ thống.

Cú pháp:

> $ git pull origin master

### 6. Push.

Là hành động đưa những thay đổi đã commit lên một branch nào đó ở remote repository hoặc một branch mới hoàn toàn lên remote repository. Sau khi push lên thì các thành viên của team có thể thấy và đồng bộ code xuống máy local.

Cú pháp push một branch có tên là `new_feature`:

> $ git push origin new_feature

### 7. Clone.

Sao chép một repository có sẵn về local.

Cú pháp:

> git clone /đường-dẫn-đến-repository/

![Alt text](image-2.png)

### 8. Fork.

**_Fork_** là hành động tạo một bản sao của repository gốc thành một repository của bạn. Việc fork một repository cho phép bạn dễ dàng chỉnh sửa, thay đổi source code mà không ảnh hưởng tới source gốc.

## III. Khi nào cần Pull Request? Cách tạo Pull Request.

Khi các thay đổi của bạn đã được commit vào branch mới, bạn có thể tạo Pull Request để gộp các thay đổi của mình vào nhánh chính của dự án. Trong quá trình tạo Pull Request, bạn sẽ cung cấp thông tin về các thay đổi của mình và mô tả về mục đích của các thay đổi đó.

**_Pull request_** được tạo ra để đưa những file source code của bạn lên 1 host chung nơi mọi người có quyền truy cập sẽ truy cập vào và cùng review, để lại comment trên những file source code đó. Lúc này thời gian review và địa điểm review source code không còn là vấn đề - đó cũng chính là mục đích tạo ra pull request.

#### Cách tạo Pull Request.

**Bước 1:** Fork dự án gốc:
- Truy cập vào dự án gốc trên GitHub.
- Nhấn vào nút “Fork” ở góc trên bên phải để sao chép dự án vào tài khoản của bạn.

**Bước 2:** Clone dự án về máy
- Truy cập vào repository đã fork trong tài khoản của bạn.
- Sao chép URL của repository.
- Mở Terminal và sử dụng lệnh git clone để clone dự án về máy.

**Bước 3:** Tạo nhánh mới
- Mở Terminal trong thư mục dự án đã clone.
- Sử dụng lệnh git checkout -b [tên_nhánh] để tạo và chuyển đổi sang một nhánh mới.

**Bước 4:** Thực hiện thay đổi
- Mở dự án trong trình chỉnh sửa mã nguồn.
- Thực hiện các thay đổi cần thiết và lưu lại.

**Bước 5:** Commit và Push
- Mở Terminal và sử dụng lệnh git add . để thêm các thay đổi vào danh sách commit.
- Sử dụng lệnh git commit -m "Mô tả commit" để commit các thay đổi đã thêm.
- Sử dụng lệnh git push origin [tên_nhánh] để đẩy thay đổi lên repository của bạn trên GitHub.

**Bước 6:** Tạo Pull Request
- Truy cập vào repository của bạn trên GitHub.
- Nhấn vào nút “Compare & pull request” bên cạnh tên nhánh của bạn.
- Điền thông tin cần thiết, mô tả về Pull Request và nhấn “Create Pull Request“.

**Bước 7:** Kiểm tra và xử lý yêu cầu chỉnh sửa
- Nhóm quản lý dự án sẽ xem xét và thảo luận về Pull Request của bạn.
- Nếu cần chỉnh sửa, bạn chỉ cần thêm commit vào nhánh đã tạo và Pull Request sẽ tự động cập nhật.

**Bước 8:** Pull Request được chấp nhận và merge
- Sau khi Pull Request đạt yêu cầu, nhóm quản lý sẽ chấp nhận và merge vào nhánh chính.
- Code của bạn đã được hợp nhất vào dự án gốc.

## IV. UML là gì? Lý do cần vẽ UML.

**_Ngôn ngữ mô hình hóa thống nhất (tiếng Anh: Unified Modeling Language, viết tắt thành UML)_** là một ngôn ngữ mô hình gồm các ký hiệu đồ họa mà các phương pháp hướng đối tượng sử dụng để thiết kế các hệ thống thông tin một cách nhanh chóng.

#### Lý do cần vẽ UML.

- Hiểu rõ và Mô Hình Hóa Yêu Cầu
Trước khi bắt đầu phát triển phần mềm, việc hiểu rõ yêu cầu là rất quan trọng. Bằng cách sử dụng các biểu đồ UML như Use Case Diagrams, bạn có thể mô tả cách hệ thống nên hoạt động và phản ứng trong các tình huống cụ thể.

- Thiết Kế Cấu Trúc và Quan Hệ Phần Mềm
UML cung cấp các biểu đồ như Class Diagrams để thiết kế cấu trúc của phần mềm. Bạn có thể mô hình hóa các lớp, đối tượng và mối quan hệ giữa chúng để tạo ra một bản thiết kế cơ bản.

- Tạo Tài Liệu Thiết Kế
UML cho phép bạn tạo ra tài liệu thiết kế quan trọng cho dự án. Các biểu đồ UML có thể được sử dụng để tạo tài liệu mô tả cấu trúc và hành vi của hệ thống, giúp cho việc triển khai dự án và giao tiếp với các bên liên quan.

- Mô Phỏng và Kiểm Tra Hệ Thống
Trong quá trình phát triển, UML cung cấp khả năng mô phỏng các phần của hệ thống. Điều này giúp kiểm tra tính đúng đắn và hiệu suất của phần mềm trước khi triển khai nó vào môi trường thực tế.

- Duy Trì và Nâng Cấp Phần Mềm
Một khi phần mềm đã được triển khai, UML vẫn đóng vai trò quan trọng trong việc duy trì và nâng cấp nó. Các biểu đồ UML có thể hỗ trợ trong việc hiểu cấu trúc hiện tại, nắm vững thay đổi cần thiết, và đảm bảo tính nhất quán trong quá trình phát triển tiếp theo.

## V. Mô hình Class Diagram, Activity Diagram.

### 1. Mô hình Class Diagram.

- **_Class diagram_** mô tả kiểu của các đối tượng trong hệ thống và các loại quan hệ khác nhau tồn tại giữa chúng.

- Là một kỹ thuật mô hình hóa tồn tại ở tất cả các phương pháp phát triển hướng đối tượng.

- Biểu đồ hay dùng nhất trong UML và gần gũi nhất với các lập trình viên.

- Giúp các lập trình viên trao đổi với nhau và hiểu rõ ý tưởng của nhau.

#### Các thành phần cơ bản của Class Diagram:

- Lớp (Class): Lớp đại diện cho một đối tượng trong hệ thống phần mềm nhằm miêu tả thuộc tính và phương thức của đối tượng đó.
- Thuộc tính (Attribute): Thuộc tính là các đặc điểm/thông tin liên quan đến một lớp. Thuộc tính có thể là các biến, hằng số, hoặc các đối tượng khác.
- Phương thức (Method):  Phương thức là các hành động hoặc chức năng mà đối tượng có thể thực hiện. Chúng mô tả cách thức xử lý dữ liệu của lớp.
- Quan hệ (Relationship):  Quan hệ là đại diện cho mối liên kết hoặc tương tác giữa các lớp trong hệ thống
- Đa số (Multiplicity): Multiplicity chỉ ra số lượng đối tượng mà một quan hệ có thể có với đối tượng khác. Nó thể hiện bằng các ký hiệu số hoặc từ khóa.
- Giao diện (Interface): Giao diện xác định các phương thức mà một lớp hoặc một nhóm lớp phải triển khai.

### 2. Activity Diagram.

**_Activity Diagram_** là một công cụ được sử dụng trong UML (Unified Modeling Language) để mô tả các hoạt động được thực hiện trong một hệ thống. Đây là cách để hình dung quá trình dữ liệu, thông tin và hoạt động giữa các đối tượng khác nhau của hệ thống.

#### Lợi ích của Activity Diagram:

- Thể hiện logic của một thuật toán.
- Mô tả các bước được thực hiện trong một UML use case.
- Minh họa quy trình nghiệp vụ hoặc quy trình làm việc giữa người dùng và hệ thống.
- Đơn giản hóa và cải thiện bất kỳ quy trình nào bằng cách làm rõ các UC phức tạp.
- Mô hình hóa các yếu tố kiến trúc phần mềm, chẳng hạn như phương pháp, chức năng và hoạt động.

#### Các thành phần trong Activity Diagram

![Alt text](image-3.png)