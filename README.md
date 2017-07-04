# zhuanSplitBundle
change the sourceCode of RN, split the bundle into base part and business part.

> 通过react-native-cli 的命令react-native， react-native init name --version="0.44.1"新的工程;
> npm remove react-native;
> 切换到npm私服的源rcnpm上，执行npm install @zz-app/react-native --save;
> cd name/node_modules
> ln -s react-native @zz-app/react-native;
> 复制如下脚本到scripts中：

    ```
    "basebundle": "react-native bundle --platform android --entry-file ./base.android.js --bundle-output ./output/base.android.bundle --manifest-output ./output/base.android.manifest.json",
    "businessbundle": "react-native bundle --entry-file ./index.android.js --platform android --bundle-output ./output/index.android.bundle --manifest-file ./output/base.android.manifest.json"
    修改index.android.js,以及base.android.js和index.ios.js中的react-native为@zz-app/react-native.
    ```

> 然后再根目录执行执行一个shell脚本，内容如下。
    ```
    rm -rf ./output
    mkdir output
    npm run basebundle
    npm run businessbundle
    ```
