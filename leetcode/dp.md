除法取模出错 q2400题 恰好移动k步
1：乘法逆元
2：背包问题的递推
for(int i = 0;i<k+1;i++){
    vc[i][0] = 1;
    for(int j = 1;j<=i;j++){
        vc[i][j] = (vc[i-1][j-1]+vc[i-1][j])%mod;
    }
}
return vc[k][cap];

注意if(false) ret = max(ret,cur)
但遍历完也没有false