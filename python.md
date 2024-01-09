# twilio服务器批量打电话

```Python
# coding:utf-8
from twilio.rest import Client  # 先导入
 
# sid和token都是在twilio网站的个人设置中看到的
account_sid ='ACa075925b5d167b0a5fd927682b80'
auth_token ='d0640e48212306c9b6f8a'
# 实例化
client = Client(account_sid, auth_token)
 
# 开始发短信
def send_msg(message):
    u'自定义短信内容message'
    msg = client.messages.create(
        to='+8617112663884',  # 要给谁发短信, 必须带区号, 中国要加上+86
        from_='+15076390672', # 你自己twilio网站申请的手机号码, 必须带上+号
        body=message  # 你的短信内容
    )
 
# 开始打电话
def call_num(number):
    u'自定义打电话的号码'
    call = client.calls.create(
        to='+86'+number,  # 要给谁打电话, 必须带区号, 中国要加上+86
        from_='+15076390672', # 你自己twilio网站申请的手机号码, 必须带上+号
        url="http://tandaishi.asia/voice.mp3" # 要播放的mp3
    )
 
if __name__ == '__main__':
    call_num("17112663884")
```

# python adb 批量打电话
```Python
# coding:utf-8
import time, os
 
def test_call_number():
    # number是个列表，直接在这里天上你想要打的号码即可
    number = [10086, 10010, 10000]
    # 直接一个for循环，循环号码
    for num in number:
        # 使用adb打电话
        os.system('adb shell am start -a android.intent.action.CALL -d tel:%s' %num)
        # 这里的sleep时间基本就是你想让通话保持的时间了
        time.sleep(3)
        os.system('adb shell input tap 145 1292')
        # 打开免提
        time.sleep(10)
        #挂断电话
        os.system('adb shell input keyevent 6') # code6是挂断
        time.sleep(4)
 
if __name__ == '__main__':
    test_call_number()

```

# 图像差异对比
```Python
# codeing = "utf-8"
import cv2 as cv
import numpy as np

def compare_img_default(img1, img2):
     # 完全比较
     difference = cv.subtract(img1, img2)
     result = not np.any(difference)
     return result

if __name__ == '__main__':
     蓝天0 = cv.imread("img/test/sk0.jpg")
     蓝天00 = cv.imread('img/test/sk00.jpg')
     蓝天0i = cv.imread('img/test/sk0i.jpg')
     print(compare_img_default(蓝天0,蓝天0i))



```

# 图像差异度对比（汉明距）

```Python
import cv2 as cv
import numpy as np 
def get_img_p_hash(img):
     """
     Get the pHash value of the image, pHash : Perceptual hash algorithm(感知哈希算法)
     :param img: img in MAT format(img = cv2.imread(image))
     :return: pHash value
     """
     hash_len = 128
     # GET Gray image
     gray_img = cv.cvtColor(img, cv.COLOR_RGB2GRAY)
     # Resize image, use the different way to get the best result
     resize_gray_img = cv.resize(gray_img, (hash_len, hash_len), cv.INTER_AREA)
     # resize_gray_img = cv.resize(gray_img, (hash_len, hash_len), cv.INTER_LANCZOS4)
     # resize_gray_img = cv.resize(gray_img, (hash_len, hash_len), cv.INTER_LINEAR)
     # resize_gray_img = cv.resize(gray_img, (hash_len, hash_len), cv.INTER_NEAREST)
     # resize_gray_img = cv.resize(gray_img, (hash_len, hash_len), cv.INTER_CUBIC)
     # Change the int of image to float, for better DCT
     h, w = resize_gray_img.shape[:2]
     vis0 = np.zeros((h, w), np.float32)
     vis0[:h, :w] = resize_gray_img
     # DCT: Discrete cosine transform(离散余弦变换)
     vis1 = cv.dct(cv.dct(vis0))
     vis1.resize(hash_len, hash_len)
     img_list = vis1.flatten()
     # Calculate the avg value
     avg = sum(img_list) * 1. / len(img_list)
     avg_list = []
     for i in img_list:
         if i < avg:
             tmp = '0'
         else:
             tmp = '1'
         avg_list.append(tmp)
     # Calculate the hash value
     p_hash_str = ''
     for x in range(0, hash_len * hash_len, 4):
         p_hash_str += '%x' % int(''.join(avg_list[x:x + 4]), 2)
     return p_hash_str
def ham_dist(x, y):
     """
     Get the hamming distance of two values.
         hamming distance(汉明距)
     :param x:
     :param y:
     :return: the hamming distance
     """
     assert len(x) == len(y)
     return sum([ch1 != ch2 for ch1, ch2 in zip(x, y)])
def compare_img_p_hash(img1, img2):
     
     hash_img1 = get_img_p_hash(img1)
     hash_img2 = get_img_p_hash(img2)
     return ham_dist(hash_img1, hash_img2)
def imread():
    for i in range (1,8):
        img = cv.imread('img/' + str(i) + '.jpg')
        dif = compare_img_p_hash(img0, img)
        print('图0对比图' + str(i) + '差异系数:' + str(dif))
if __name__ == '__main__':
    img0 = cv.imread('img/0.jpg') # 该图为参考图
    print('''差异系数越大,图片差异越大.
    输出结果=====>>''')
    imread()
```



