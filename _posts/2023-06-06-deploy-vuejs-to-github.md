---
layout: post
title: Deploy VueJs lên Github
subtitle: Hướng dẫn deploy VueJs lên Github sử dụng Github pages
thumbnail-img: /assets/img/deploy-vue-to-github/deploy-vue-to-github-avatar.jpg
tags: [Deploy, Deploy VueJs, VueJs, Github page, Deploy VueJs to Github]
comments: true
---

![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-avatar.jpg)

<br/><br/>

**Github.IO** là nơi chúng ta có thể hosting các project free trực tiếp từ các repository trên github.com. Ở **Github.io** các bạn có thể hosting các trang web như profile cá nhân, landing page, hay các trang giới thiệu sản phẩm/project,…

Hôm nay mình sẽ hướng dẫn các bạn cách **deploy VueJS project lên github.io**, nhờ đó các bạn có thể hosting project VueJS của mình một cách nhanh chóng và hoàn toàn miễn phí.

<br/>

# **Tạo project**

Đầu tiên các bạn cần phải cài vue-cli nhé. nếu bạn chưa có thì có thể chạy lệnh cmd sau:

```
npm install -g @vue/clivue-cli
```

Sau đó chúng ta sẽ cùng tạo một project mới bằng vue-cli:
```
vue create deploy_vue_to_github
```

<br/>

# **Test project**
Sau khi tạo thành công project Vue, các bạn kéo thư mục chứa project vào Visual Code hoặc bất kỳ IDE nào các bạn đang code Vue

Sau đó các bạn mở terminal trên IDE, gõ lệnh:
```
npm run serve
```
Khi run thành công thì được giống ảnh bên dưới
![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-1.png)

Sau đó các bạn mở URL khi run thành công lên browser

Lúc này URL là localhost, nếu trên trình duyệt chạy ok tức là project bạn không có vấn đề gì :v
![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-2.png)

<br/>

# **Build project**
Quay lại IDE, các bạn tắt chương trình đang run và mở file vue.config.js để sửa như sau:

``` js
module.exports = {
  publicPath: process.env.NODE_ENV === 'production'
    ? '/deploy_vue_to_github/' // Thay tên repository của các bạn trên muốn deploy
    : '/'
}
```

Sau khi sửa xong các bạn save file lại và quay lại terminal IDE nhập lệnh build như sau:
```
npm run build
```

|![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-3.png)|
|:--:|
|*Ảnh minh họa cho 2 bước trên*|


Quá trình build diễn ra trong 1 vài phút tùy vào project to hay nhỏ. Sau khi build thành công thì trong project Vue của bạn xuất hiện thư mục dist, trong thư mục dist chứa các file html/css và js. Nếu bạn nào không có thì có thể thực hiện lại bước build

Sau khi buil thành công, ở terminal các bạn nhập lần lượt các lệnh sau:
```js
cd dist
git init
git add -A
git commit -m "deploy_vue_to_github"
git push -f https://github.com/<tên user github>/<tên repo>.git master:gh-pages
```

![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-4.png)

Sau khi push thành công lên github, các bạn quay lại repository của các bạn trên github. Vào tab Actions để xem quá trình deploy, tất cả các bước có màu xanh lá cây tức là deloy thành công

![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-5.png)

Cuối cùng là mở trình duyệt tại địa chỉ: https://<tên user github>.github.io/<tên repo>/ (ví dụ như của mình là https://buiquanghieu2910.github.io/deploy_vue_to_github). Và cuối cùng là xem kết quả

|![Image](/assets/img/deploy-vue-to-github/deploy-vue-to-github-6.png)|
|:--:|
|***Chúc các bạn thành công !!!***|
