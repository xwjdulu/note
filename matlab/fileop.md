fid = fopen('exp.txt', 'wt');
fprintf(fid, '%d %d\n', x);
fclose(fid);
使用追加模式打开文件
fid = fopen('exp.txt', 'at+');