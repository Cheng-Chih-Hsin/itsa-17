#include<stdio.h>  
#include<string.h>  
#include<ctype.h>  
int main() {
    char enter[10000];
    fgets(enter, 9999, stdin);//使用 fgets 函數讀取一行最多 9999 個字符，存儲到 enter 陣列中
    int len = strlen(enter);//使用 strlen 函數獲取 enter 陣列的長度
    for (int i = 0; i < len; i++) {
        enter[i] = tolower(enter[i]);//使用 tolower 函數將 enter 陣列中的英文字母轉換為小寫
    }
    char ans[1000][1000];
    int nowAns = 0;
    char* pch = strtok(enter, " \r\n");//使用 strtok 函數將 enter 陣列中的單詞逐個分割出來，並依次判斷是否已經存儲到 ans 二維陣列中
    while (pch != NULL) {
        int judge = 1;
        for (int i = 0; i < nowAns; i++) {
            if (strcmp(ans[i], pch) == 0) {//如果該單詞還沒有存儲到 ans 二維陣列中，則存儲到 ans 二維陣列中
                judge = 0;
                break;
            }
        }
        if (judge) {
            strcpy(ans[nowAns], pch);//最後將 ans 二維陣列中存儲的所有單詞輸出到標準輸出
            nowAns++;
        }
        pch = strtok(NULL, " \r\n");
    }
    for (int i = 0; i < nowAns; i++) {
        if (i)
            printf(" ");
        printf("%s", ans[i]);
    }
    printf("\n");
    return 0;
}
