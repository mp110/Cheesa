# Cheesa
Cheesa
import random

# Danh sách phần thưởng trong blind box
rewards = [
    "Hộp quà vàng",
    "Hộp quà bạc",
    "Hộp quà kim cương",
    "Vé quay thêm",
    "Voucher giảm giá 20%",
    "Huy hiệu đặc biệt"
]

def open_blind_box():
    reward = random.choice(rewards)
    print("Chúc mừng bạn nhận được:", reward)

if __name__ == "__main__":
    print("Chào mừng bạn đến với chương trình Blind Box!")
    input("Nhấn Enter để mở hộp: ")
    open_blind_box()
