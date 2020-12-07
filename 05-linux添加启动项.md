### linux中，在菜单栏中添加typora的启动项

1. #### 编写typora.desktop文件

   ```bash
   [Desktop Entry]
   Type=Application
   Name=typora
   Comment=typora for edit
   Exec=/home/cyan/software/typora/Typora
   Icon=/home/cyan/software/typora/icon_128x128.png
   Terminal=flase
   Catergories=Development;Editor;
   Name[en_US]=typora
   ```

2. #### 将编写好的typora.desktop放到/usr/share/applications文件夹下

```bash
sudo cp typora.desktop /usr/share/applications
```

