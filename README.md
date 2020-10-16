# Multi-Agent-Search
Bài tập AI

## Question 1 (4 points): Reflex Agent
Cách làm: Ta gọi cost là khoảng cách nhỏ nhất từ vị trí mới của pacman đến vị trí thức ăn. Sau đó tìm khoảng cách nhỏ nhất từ vị trí pacman đến vị trí của những con ma, nếu khoảng cách đó <= 1(tức là bước tiếp theo sẽ chạm vào con ma) thì cost sẽ là vô cùng. Kết quả cuối cùng sẽ là successorGameState.getScore() + 1.0/cost ( ta ưu tiên ăn thức ăn ở gần trước).
## Question 2 (5 points): Minimax
Cách làm: Ta sử dụng đệ quy để tính max của pacman và min của những con ma. Trong hàm tính max ta lại gọi đến hàm tính min của những con ma và cập nhập kết quả vào max. Khi đến hàm tính min, nếu chưa phải con ma cuối cùng thì ta tiếp tục tính min so với con ma tiếp theo. Nếu đó là con ma cuối cùng thì ta lại gọi lại hàm tính max của pacman. Hàm đệ quy dừng lại khi không có hành động nào hoặc pacman thắng hoặc pacman thua.
## Question 3 (5 points): Alpha-Beta Pruning
Cách làm: Ban đầu ta khởi tạo giá trị alpha = -oo, beta = oo. Ta sử dụng đệ quy như bài 2 nhưng thay vào đó, trong hàm tính max, ta cập nhật alpha = max(alpha, cost) , nếu cost > beta thì dừng đệ quy.Tương tự với hàm tìm min, ta cập nhật beta = min(beta, cost), nếu cost < alpha thì dừng đệ quy.
## Question 4 (5 points): Expectimax
Cách làm: Tương tự như bài 2. Chỉ khác là, trong hàm tính min, ta sẽ trả về không phải là giá trị nhỏ nhất mà là giá trị trung bình của những con ma.
## Question 5 (6 points): Evaluation Function
Cách làm: Ta gọi cost là khoảng cách nhỏ nhất từ vị trí của pacman đến vị trí có thức ăn. Sau đó ta tính khoảng cách từ vị trí pacman đến vị trí các con ma. Nếu khoảng cách này = 0 và thời gian con ma đó sợ = 0 thì cost = vô cùng. Nếu khoảng cách = 1 và thời gian ma sợ = 0 thì cost -= 1000. Nếu khoảng cách nhỏ hơn thời gian ma sợ thì cost += 50. Kết quả cuối cùng là currentGameState.getScore() + 1.0/(cost) (ta vẫn ưu tiên ăn thức ăn ở gần trước)
