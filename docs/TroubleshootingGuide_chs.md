## [ZENCash](https://zensystem.io/) Desktop GUI Wallet troubleshooting guide     ZenCash Windows桌面图形界面版钱包故障排查向导

![Screenshot1](ZENChat_small.png "Chat Window") ![Screenshot1](ZENCashWalletMac_0.74.7_small.png "Wallet Window") 

This document outlines possible solutions to several common problems that user might encounter while using the wallet.本文描述用户使用钱包时遇到的几个普通问题的几个可能的解决办法。

### How to diagnose wallet problems 怎样诊断钱包问题

When wallet problems occur, the information about the errors that caused the issue is usually found in the log files written by the wallet itself and also by `zend`. The location of the wallet log files is:

当钱包问题出现时，引起问题的错误的信息通常能够在日志中找到，这些日志通常由钱包自己或由zend生成，钱包日志位置在（根据你用的系统具体看）：
```
Linux:    ~/.ZENCashSwingWalletUI/ZENCashGUIWallet_xxxx_xx_debug.log 
Windows:  %LOCALAPPDATA%/ZENCashSwingWalletUI/ZENCashGUIWallet_xxxx_xx_debug.log
Mac OS:   ~/Library/Application Support/ZENCashSwingWalletUI/ZENCashGUIWallet_xxxx_xx_debug.log
```
`zend` that is automatically started by the wallet, stores its logs at locations:

zend由钱包自动启动，存其日志在（根据你用的系统具体看）：
```
Linux:    ~/.zen/debug.log, 
Windows:  %APPDATA%/Zen/debug.log
Mac OS:   ~/Library/Application Support/Zen/debug.log
 ```
The log files are the first place too look for clues as to the nature of problem.

要找到问题根源线索，日志文件是第一个要去找的地方。

### Common Problem 1 - wallet fails during start up
普通问题1 - 钱包启动失败

This kind of problem may have multiple causes but the most frequent one in practice is that `zend` fails to start properly. The latter is in turn most commonly caused by block-chain corruption. This could occur 
in rare cases when for instance machines are stopped due to power disruptions, while `zend` is writing data.

这种问题可能有多方面的原因，但实践中，最可能是zend不能正确启动，其次可能是由于区块链出错引起。极少案例中，zend正在写数据，实例机器因电力中断导致停机。


A common symptom of this problem is an error message like: 

一般的错误信息截图如下：
![Screenshot1](EOF_error.png "Chat Window") 

The reason is usually that `zend` has not started properly and the GUI wallet cannot connect to it. As a start
one may examine the `zend` logs to find the technical details of the problem. One way to fix this problem, that 
works in 90%+ of cases is to start `zend` manually with a `-reindex` option from a terminal and start the GUI wallet only after that. The command is:

原因通常是，zend没有正确启动，图形界面钱包连接不上它。首先要检查zend日志以找到问题的技术细节。修复此问题的一个方式（这种方式在90%的案例中管用）是在terminal中带-reindex参数来手动启动，，然后再启动图形界面，命令如下：

```
zend -reindex
```
For non-technical users here is some information on how to open a terminal on [Windows](https://www.lifewire.com/how-to-open-command-prompt-2618089) and [Mac OS](https://www.wikihow.com/Open-a-Terminal-Window-in-Mac). The full command on Mac OS is:

对于非技术用户，这是一些如何在windows和mac os中打开terminal的信息，mac os中完整命令为：

```
/Applications/ZENCashWallet.app/Contents/Java/zend -reindex
```
On Windows you first have to locate `zend.exe`. It is in the `/app` sub-directory of the wallet installation.

在Windows中，你首先必须定位到zend.exe.它在钱包安装的目录的`/app` 子目录中。

### Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
