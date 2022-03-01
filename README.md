# 封鎖網頁小遊戲
這項專案主要的開發動機是因同學會使用班級電腦作不適當用途（指教學以外之用途，如使用社群軟體及遊玩網頁遊戲），為"制裁"那些同學，減少此類情形發生，因而產生這項專案。

## 作業環境
- Linux系統
- bind 8 或以上版本

## 使用方式
在安裝完作業環境後，請先關閉bind軟體。並將專案中的`BlockDNSHost.conf`與`BlockDNSHost.hosts`複製至`/etc/bind/`。並於目錄中的`named.conf.options`於`options{}`區段新增如下資料（您也可以自行修改轉送DNS伺服器）。
```
options {
    .
    .
    .

    allow-recursion { any; };
	forward first;
	forwarders {
		8.8.8.8;
		8.8.4.4;
		1.1.1.1;
		2001:4860:4860::8888;
		2001:4860:4860::8844;
	};
};
```
並且於文件最一行新增如下資料。
```
    include "/etc/bind/BlockDNSHost.conf";
```
修改完畢後即可重新啟動bind軟體。

## 關於`GooreplacerMode.old`
這個資料夾為舊方法，無法使用動態更新且僅限一瀏覽器使用，因此已被廢棄。但檔案留存以備不時之需。

# Web Game Blocker
The main motivation of this project is that the students will use the class computer for inappropriate purposes (referring to purposes other than teaching, such as using social website and playing web games), in order to "sanction" those students and reduce the occurrence of such situations. I generate this project.

## Environment
- Linux operating system
- bind 8 or newer versions

## Usage
After installing the environment, please close the bind software first. Copy `BlockDNSHost.conf` and `BlockDNSHost.hosts` in the project to `/etc/bind/`. And add the following information in the `options{}` section of `named.conf.options` in the directory (you can also modify the forwarding DNS server by yourself). 
```
options {
    .
    .
    .

    allow-recursion { any; };
	forward first;
	forwarders {
		8.8.8.8;
		8.8.4.4;
		1.1.1.1;
		2001:4860:4860::8888;
		2001:4860:4860::8844;
	};
};
```
And add the following information at the last line of the document.
```
    include "/etc/bind/BlockDNSHost.conf";
```
After modification, you can restart the bind software.

## About `GooreplacerMode.old`
This method is old, cannot use dynamic updates and it's only available to one browser, so it has been deprecated. But the file is kept for emergencies.
