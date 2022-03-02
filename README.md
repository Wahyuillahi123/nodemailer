# nodemailer
nodemailer adalah fitur verifikasi pada nodejs, untuk mengirimkan pesan email secara otomatis pada vps server.
jika kamu kesulitan dalam memahami fitur ini, mampir di halaman ini adalah langkah yang tepat.

# Instal NPM
``` html
   $ npm i nodemailer
```

sebagai contoh disini saya akan menggunakan fitur ini sebagai langkah verifikasi email kepada setiap user yang melakukan register di halaman website saya.

# Login Akun Google (Gmail)
pada bagian ini pastikan email dan password benar, dan akun tidak dalam privat (keamanan lebih dari 1)

``` html
var nodemailer = require('nodemailer');

//bagian email;
var transporter=nodemailer.createTransport({
  service:'gmail',
  auth:{
    user:'masukan.email@gmail.com',
    pass:'masukan.password'
  }
});

```

# Router Login
pada bagian ini bertujuan agar mengirimkan email verifikasi kepada user setiap kali melakukan login selama akun belum di verifikasi.

``` html
	//kirimkan aktifasi ke akun emailnya, agar dia bisa aktif;
          var jasaku="http://jasakumedia.id/konfirmasi/gmail/"+users._id;
          
          var mailOptions={
            from:'wahyuillahi.19990@gmail.com',
            to:users.email,
            subject:users.name+' aktifasi',
            // text:'Silahkan klik link berikut untuk melakukan aktifasi akun anda https://jasakumedia.herokuapp.com/'+users._id
            html:"Hallo "+users.name+" silahkan klik tombol aktif untuk mengaktifkan akun kamu " + "<a href='"+jasaku+"'>Verifikasi</a>"
          };

          transporter.sendMail(mailOptions,(err,info)=>{
            if(err)throw err;
            console.log('Email sent: '+info.response);
          });
```

# Cara Pakai
- Buat akun user nonaktif setelah melakukan register
- setelah menerima pesan verifikasi aktifkan akun user dengan sistem update

# Support
Follow my instagram : https://www.instagram.com/wahyu_illahi07/ 
Youtube Channel : https://www.youtube.com/playlist?list=PL2DC6n3PrEKVXN9nvzONe9idXa9BgCusj
