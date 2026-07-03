# LexSheet — 律师计费与账单管理软件

## 安装与使用教程

本教程介绍如何在一台 Windows 电脑上安装并运行 LexSheet，以及团队成员如何日常使用。如安装或使用过程中遇到问题，欢迎联系开发者获取协助：**lexsheet@outlook.com** 用户通过邮件主动提供的信息（包括截图）仅用于问题诊断，问题解决后即予删除，不作任何其他用途。

遇到不易书面描述的复杂问题时，建议将截图发送至开发者邮箱，方便开发者诊断问题并及时更新软件。发送截图前请注意检查画面内容，避免截图中包含客户姓名、案件信息等敏感数据。

*关于本软件：本工具专为律师小团队的实际工作需求设计，核心功能逻辑由具备法律业务实践经验的人员主导设计，开发过程中借助 AI 辅助完成代码实现。诚挚欢迎使用者对软件功能提出意见和建议。*

---

## 为什么选择本软件？

本软件专为律师小团队设计，有以下核心优势：

- **专注核心功能，没有冗余**：只做工时记录与账单管理，功能简洁实用
- **数据完全本地存储，开发者零收集**：所有数据（包括客户信息、工时记录和账单）仅保存在您自己的设备上。本软件不向开发者或任何第三方收集、传输或发送任何数据
- **目前免费提供下载使用**：无订阅费、无月费，无需激活码，安装后即可使用

---

## 一、软件简介

*本教程内容仅为操作说明，不构成对软件功能或效果的任何保证。软件按"现状"提供，详见随附的 LICENSE 文件。*

本软件是一款面向律师小团队设计的本地化计时与账单管理工具，主要功能包括：

- 团队成员录入每日工作时间及垫付费用支出（按客户/项目分类）
- 管理员（合伙人/行政人员）管理客户、项目、律师及团队账号
- 一键生成符合律所格式要求的工时单（Timesheet）和账单（Invoice），支持叠加律所抬头纸；也可生成无抬头纸的 Word 版账单，方便自行编辑排版或套用自己的模板
- 账单生成前设有合伙人手动调整环节，支持灵活调整工时费（Fees）及垫付费用（Disbursements）金额
- 基于角色的权限管理：管理员可查看全部数据，普通成员仅可管理自己的工时和费用记录
- 工时记录自动锁定保护机制，账单出具后自动锁定对应工时及费用记录，防止通过软件界面进行事后修改
- 完整的操作审计日志，记录所有关键操作（含工时删改、费用删改、账单生成与作废、付款状态更新等），支持导出为 Excel 文件
- 应收账款追踪：对已出具账单可记录付款状态（未付/部分付/已付），超过30天未收款自动标红提醒
- 支持团队成员通过安全组网工具远程访问，无需公网服务器（详见第五章）

---

## 二、安装前准备

### 2.1 选择一台作为服务器的电脑

建议选择一台可以长期开机的电脑（如办公室闲置主机、迷你电脑）作为服务器，安装本软件后，团队其他成员通过浏览器访问这台电脑，无需在自己电脑上安装任何东西（如需在办公室局域网外使用本软件，团队成员设备仅需安装远程访问工具，见第五章）。

*注意：本软件的**安装包仅需**在"服务器"这台电脑上运行一次。团队其他成员不需要运行安装包。*

### 2.2 系统要求

- 操作系统：Windows 10 / 11（64位）
- 不需要提前安装 Node.js 或其他开发工具，安装包已自带运行环境
- 建议预留至少 500MB 磁盘空间
- 软件本身的运行不需要联网（全部数据存储和处理均在本地完成）。安装过程中需要联网下载部分组件；团队成员希望在办公室局域网以外的地方访问软件时，则需要联网（局域网内访问不需要联网，详见第五章）

---

## 三、安装步骤

- 双击运行安装包文件（文件名类似 LexSheet-Setup.exe）。
- 如系统弹出"用户账户控制"提示，点击"是"以允许安装程序获取必要权限。
- 安装程序启动后，首先弹出**语言选择对话框**，请选择"中文（简体）"或"English"。
- 在欢迎界面点击"下一步"，选择安装位置。**强烈建议保持默认路径（C:\LexSheet）不变。** 如确需更改，请选择您拥有完整读写权限的自定义位置（如 D:\LexSheet）。**切勿将软件安装至 C:\Program Files 或 C:\Program Files (x86)**——Windows 对这些目录有写入保护，软件启动后将无法创建数据库文件，导致无法正常使用。
- 阅读许可协议，点击"我同意此协议"后方可继续。
- 勾选"自动配置防火墙规则"选项（建议保持勾选，这样团队成员才能从其他设备访问）。
- 点击"安装"，安装程序将自动完成以下工作：解压程序文件、配置运行环境、安装必要组件。**首次安装时，系统需要从网络下载若干运行组件，根据网络和电脑情况不同，此过程通常需要3至5分钟，请耐心等待，不要关闭安装窗口。**
- 安装完成后，点击"完成"。

*注意：如果这台电脑此前已经使用过本软件并保留有历史数据库文件，安装程序会自动检测并提示，不会覆盖已有数据。*

---

## 四、首次启动

- 在安装目录中找到 start.bat 文件，双击运行。
- 软件启动需等待约 1 分钟，命令行窗口显示"Ready"字样即表示服务已启动。启动过程中命令行窗口可能出现少量技术性提示信息，这是正常现象，不影响功能。
- 保持该窗口开启（不要关闭），这个窗口代表软件正在后台运行。
- 在浏览器中输入 http://localhost:3000，直接进入登录页面。
- 使用默认管理员账号登录：用户名 admin，密码 admin123。
- 首次登录会强制要求修改密码，请设置一个新密码并妥善保管。

*注意：start.bat 窗口必须保持开启状态，软件才能持续运行。如果需要关闭电脑或暂停使用，可以直接关闭该窗口；下次使用前重新双击 start.bat 即可。*

*安全提示：软件首次启动后，请先在本机完成首次登录并修改默认密码，再将软件地址告知团队成员或配置远程访问工具。在默认密码修改完成之前，任何能访问该地址的人均可用默认账号登录。*

---

## 五、团队成员远程访问设置

如果团队成员需要在办公室以外的地方（如出差、在家）使用本软件，需要借助第三方安全组网工具，在各设备之间建立加密连接，无需公网服务器。

**关于工具选择的重要说明：**

本章以 **Tailscale** 为例介绍配置步骤，但用户可根据自身情况选择其他工具（如 ZeroTier 等）。选择何种远程访问工具、以及该工具的使用是否符合其服务条款，由使用者自行判断和负责，与本软件及其开发者无关。

具体而言，Tailscale 的免费（Personal）计划按其服务条款仅限个人非商业用途；律所用于商业业务的，建议升级至 Tailscale 付费计划，或使用其他工具。ZeroTier 的免费计划对商业用途限制相对较少，但初次配置步骤略多，需要使用者具备一定技术能力。

*注意：远程访问工具并非本软件运行的必要条件，仅用于解决"局域网外远程访问"这一需求。如果团队成员始终在同一办公室局域网内使用本软件，可以直接通过服务器的局域网 IP 地址访问，完全不需要安装任何远程访问工具。*

### 5.1 服务器端设置（以 Tailscale 为例，仅需设置一次）

- 访问 tailscale.com 下载并安装 Tailscale。
- 使用电子邮箱注册账号并登录。
- 登录成功后，右键点击系统托盘中的 Tailscale 图标，记下显示的 IP 地址（格式类似 100.x.x.x）。

### 5.2 团队成员设置

- 管理员登录 Tailscale 管理后台（login.tailscale.com/admin/users），邀请每位团队成员的邮箱加入同一个网络。
- 团队成员收到邀请后，在自己的电脑或手机上下载安装 Tailscale，并使用受邀邮箱登录（务必使用收到邀请的邮箱，而非其他个人邮箱）。
- 登录成功后，在浏览器中输入 http://[服务器的Tailscale IP]:3000 即可访问，例如 http://100.100.220.56:3000。

*注意：无论身处何地，只要团队成员设备上的 Tailscale 处于已连接状态，即可**正常访问**本软件，效果等同于在同一局域网内。*

---

## 六、管理员日常操作指南

### 6.1 初始设置

- 登录后进入"Settings"页面，填写律所基本信息（律所名称、银行账户信息、管理费率、税率等）。管理费率和税率无预设值，请根据律所实际情况填写；如不需要收取，填写 0 即可。
- 如有律所专用抬头纸（PDF格式），可在该页面上传，账单将自动叠加在抬头纸上生成。
- 进入"Lawyers"页面，添加团队律师及其计费费率。
- 进入"Clients & Projects"页面，添加客户信息。在每个项目信息页面，可填写该项目对应的聘用协议签署日期（Engagement Letter Date），将自动体现在账单 Re: 行中。可在"Billing Arrangement"区块填写计费安排说明（仅供参考，不影响账单自动计算）。
- 进入"Users"页面，为每位团队成员创建登录账号，并关联其律师身份，分配可访问的项目。

### 6.2 生成账单

账单生成分为以下步骤：

1. 进入"Settings & Export"页面，选择需要出具账单的项目，填写本次账单的截止日期。
2. 系统自动显示工时明细预览，核对无误后点击"Proceed to Adjustment"进入金额调整页面。
3. 在调整页面，合伙人可查看该项目未结算费用的参考汇总，并在 Disbursements 栏填入换算为账单币种后的垫付费用总额；如有需要，也可修改 Fees（工时费）金额。General Expenses 和 Local Tax 将自动实时计算。
4. 确认全部金额无误后，点击"Download Invoice (PDF)"生成正式账单并下载。生成后对应的工时记录和费用记录将自动永久锁定。
5. 如需在提交前自行编辑格式，可点击"Download Invoice (Word, no letterhead)"下载 Word 版本，该操作**不会锁定**任何记录。

*注意：如发现已生成的账单存在错误，可前往"Invoice History"页面作废对应账单，相关记录将自动解锁，可重新生成。*

### 6.3 应收账款管理

- 进入"Invoice History"页面，可查看所有已出具账单的付款状态（Unpaid / Partial / Paid）。
- 点击付款状态徽标，可更新收款状态、已收金额、收款日期及备注。
- 超过 30 天未收款的账单会显示红色逾期警示，逾期天数以**账单出具日**为起算点，可通过筛选"Overdue"快速定位。
- 已作废的账单不显示付款状态。

### 6.4 数据备份

- 进入"Settings"页面，找到"Data Backup"区块，点击"Download Backup"按钮。
- 系统将提示您选择保存位置，打包完成后自动下载为 zip 压缩包（文件名格式：LexSheet-Backup-YYYY-MM-DD.zip）。
- 建议定期备份并将 zip 文件保存至安全位置（如外部硬盘或云存储）。

*注意：如需恢复数据，请关闭软件（关闭 start.bat 窗口），解压备份文件，将解压出的所有文件复制到安装目录（覆盖同名文件），然后重新启动软件（运行 start.bat）。*

*关于数据迁移：如将来决定停止使用本软件，工时记录和费用记录可下载为 Excel 文件；历史账单已保存为 PDF/Word 文件；数据库备份文件可作为完整存档长期保留。您的数据不会被锁定在本软件中。*

### 6.5 审计日志

- 进入"Audit Log"页面（管理员专属），可查看所有关键操作的完整记录。
- 支持按操作类型和日期范围筛选。
- 点击"Export Current View"可将当前筛选结果导出为 Excel 文件。未设置筛选条件时，导出全部审计日志；设置了筛选条件后，仅导出当前显示的记录。
- 审计日志不可通过软件界面编辑或删除，所有条目持久保存。

---

## 七、团队成员日常操作指南

- 在浏览器中打开软件地址，使用管理员分配的账号登录。
- 首次登录后，建议前往导航栏的密码修改入口设置自己的密码。
- 在首页"Time Entries"标签下录入每日工作时间：选择项目、填写工作内容描述、填写工时小时数。
- 在"Expenses"标签下录入垫付费用：选择项目、选择费用类别、填写金额及币种。
- 可在"My Entries"和"My Expenses"表格中查看、编辑或删除自己的未锁定记录。
- 可随时下载自己的工时清单（Excel 格式）和费用清单（Excel 格式）。

*注意：工时记录在工作发生日满 10 天后将自动锁定，无法再修改或删除。如确有必要修改已锁定的记录，请联系管理员协助解锁。*

---

## 八、常见问题

**Q：忘记密码怎么办？**

普通成员请联系管理员，管理员可在"Users"页面为您重置密码。

管理员如忘记密码，可使用每次修改密码时系统生成的**恢复码**重置。在登录页面点击"Forgot password?"，输入用户名和恢复码，即可设置新密码。恢复码在每次修改密码后显示一次，请妥善保存。

**如恢复码也已丢失：** 由于本软件采用零数据收集架构，开发者无法获取、也无法核实任何用户的身份信息，因此**无法在恢复码丢失的情况下为您验证管理员身份并提供密码重置服务**。妥善保管恢复码是管理员的责任，请务必重视。

**Q：浏览器打不开软件页面怎么办？**

- 确认服务器电脑上的 start.bat 窗口是否仍在运行
- 确认访问地址是否正确（本机访问用 localhost，远程访问用组网工具分配的 IP）
- 如使用 Tailscale，确认自己的设备是否显示"已连接"状态

**Q：远程访问时浏览器显示"HTTP ERROR 502"怎么办？**

如电脑安装了 Clash 等代理软件并开启了"TUN 模式"，可能导致 502 错误。解决方法：临时关闭 TUN 模式，或将组网工具网段（Tailscale 为 100.64.0.0/10）加入代理软件的"绕过/Bypass"名单。

**Q：如何备份数据？**

请使用 Settings 页面"Data Backup"区块中的"Download Backup"按钮，选择保存位置后系统会自动打包数据库文件。建议定期备份并妥善保存。

**Q：服务器电脑出现故障怎么办？**

在新电脑上重新运行安装包，再将备份 zip 文件解压，将全部文件复制到新安装目录中覆盖，重新运行 start.bat 即可恢复全部历史数据。

**Q：命令行窗口中出现警告信息是否影响使用？**

不影响。显示"Ready"字样即表示运行正常。

---

*如在安装或使用过程中遇到本教程未覆盖的问题，请联系开发者：lexsheet@outlook.com*

---
---

# LexSheet — Legal Billing & Time Tracking Software

## Installation & User Guide

This guide explains how to install and run LexSheet on a Windows computer, and how team members can use it on a daily basis. If you encounter any issues, please contact the developer: **lexsheet@outlook.com** Any information voluntarily submitted via email (including screenshots) is used solely for diagnosing the reported issue and is deleted once resolved.

For complex issues that are difficult to describe in writing, a screenshot sent to the developer's email is the most efficient way to get help. Before sending, please ensure no client names or case information are visible in the screenshot.

*About this software: LexSheet was designed around the practical billing and time-tracking needs of small legal teams, with core product logic developed by someone with direct experience in legal practice, and implementation assisted by AI. Feedback and feature suggestions are warmly welcome.*

---

## Why LexSheet?

LexSheet is designed for small legal teams and offers three core advantages:

- **Focused on what matters, nothing more**: Built exclusively for time tracking and billing — simple and practical
- **All data stays on your device — the developer collects nothing**: All data, including client information, time records, and invoices, is stored exclusively on your own device. The Software does not collect, transmit, or send any data to the developer or to any third party
- **Currently free to download and use**: No subscription, no monthly fee, no activation code required

---

## I. Overview

*This guide is provided for informational purposes only and does not constitute a warranty of any kind regarding the Software's functionality or performance. The Software is provided "as is"; see the accompanying LICENSE for full terms.*

LexSheet is a self-hosted time tracking and billing tool for small legal teams. Key features include:

- Team members log daily billable hours and expenses by client/matter
- Administrators (partners/management) manage clients, matters, lawyers, and user accounts
- Generate professional timesheets and invoices with optional firm letterhead overlay; Word (.docx) output also available for manual formatting
- Partner adjustment step before invoice finalisation — manually set fees and disbursement amounts
- Role-based access: administrators see all data; normal users manage only their own time and expenses
- Automatic time entry locking to prevent backdating through the application interface; records locked durably after invoice generation
- Full audit log of all key operations, exportable to Excel
- Accounts receivable tracking: record payment status (Unpaid / Partial / Paid) per invoice; automatic overdue flagging after 30 days
- Team members can access the software remotely via a secure networking tool (see Chapter V)

---

## II. Before You Begin

### 2.1 Choosing a server machine

We recommend designating one computer (e.g. an office desktop or mini PC) as the server. After installation, team members access the software through their browsers — no installation required on their devices. For access outside the office network, team members only need to install a remote access tool (see Chapter V).

*Note: The installer only needs to be run once, on the server machine. Other team members do not need to run the installer.*

### 2.2 System requirements

- Operating system: Windows 10 / 11 (64-bit)
- No need to pre-install Node.js or any development tools — the installer includes the runtime environment
- At least 500 MB of free disk space recommended
- The software runs entirely offline after installation. An internet connection is required during installation to download certain components, and for remote access outside the local network (see Chapter V)

---

## III. Installation

- Double-click the installer file (e.g. LexSheet-Setup.exe).
- If a User Account Control prompt appears, click Yes to allow the installer to proceed.
- When the installer starts, a **language selection dialog** appears — select "中文（简体）" or "English".
- On the welcome screen, click Next and choose an installation directory. **We strongly recommend keeping the default path (C:\LexSheet) unchanged.** If you need to change it, choose a location where you have full read and write access (e.g. D:\LexSheet). **Do not install to C:\Program Files or C:\Program Files (x86)** — Windows restricts write access to these directories, which will prevent the software from creating its database file and cause it to fail on startup.
- Read the License Agreement and select "I accept the agreement" to continue.
- Keep the "Configure firewall rules automatically" option checked — this allows team members to access the software from other devices on the network.
- Click Install. The installer will extract files, configure the runtime, and install required components. **On first installation, certain components are downloaded from the internet. This typically takes 3 to 5 minutes — please wait and do not close the installer window.**
- When installation is complete, click Finish.

*Note: If this machine was previously used with LexSheet and a database file already exists, the installer will detect it and will not overwrite your existing data.*

---

## IV. First Launch

- In the installation directory, double-click `start.bat`.
- The software takes about 1 minute to start. When the command prompt window shows "Ready", the server is running. Some technical messages may appear during startup — this is normal and does not affect functionality.
- Keep this window open. It represents the software running in the background.
- Open your browser and go to http://localhost:3000. You will be taken directly to the login page.
- Log in with the default administrator credentials: username `admin`, password `admin123`.
- You will be prompted to change your password on first login. Please set a strong password and keep it safe.

*Note: The start.bat window must remain open for the software to keep running. To stop the software, close this window. To start it again, double-click start.bat.*

*Security note: After launching the software for the first time, complete your first login and change the default password on the server machine before sharing the server address with team members or configuring any remote access tools. Until the default password is changed, anyone who can reach the server address can log in with the default credentials.*

---

## V. Remote Access for Team Members

If team members need to access the software from outside the office (e.g. when travelling or working from home), a third-party secure networking tool is required to establish an encrypted connection between devices, without needing a public-facing server.

**Important note on tool selection:**

This chapter uses **Tailscale** as an example, but users may choose any suitable alternative (e.g. ZeroTier). The choice of remote access tool and compliance with its terms of service is the user's sole responsibility and has no relation to this software or its developer.

Specifically, Tailscale's free Personal plan is intended for non-commercial use under its terms of service. Law firms using the software for commercial purposes should consider upgrading to a paid Tailscale plan or using an alternative tool. ZeroTier's free plan has fewer commercial use restrictions, though the initial setup is more involved.

*Note: A remote access tool is not required to run LexSheet — it is only needed for access outside the local office network. If all team members are always on the same network, they can access the software directly via the server's local IP address with no additional tools required.*

### 5.1 Server-side setup (Tailscale example — one-time)

- Visit tailscale.com, download and install Tailscale.
- Register and log in with an email address.
- After logging in, right-click the Tailscale icon in the system tray and note the IP address shown (format: 100.x.x.x).

### 5.2 Team member setup

- The administrator logs in to the Tailscale admin console (login.tailscale.com/admin/users) and invites each team member's email address.
- Team members download and install Tailscale on their device, and log in using the invited email address.
- Once connected, open a browser and go to http://[server Tailscale IP]:3000 — for example, http://100.100.220.56:3000.

*Note: As long as Tailscale is connected on the team member's device, the software is accessible from anywhere — just as if they were on the same local network.*

---

## VI. Administrator Guide

### 6.1 Initial setup

- After logging in, go to the Settings page and enter your firm's details (firm name, bank account information, administrative expense rate, tax rate, etc.). Rates have no pre-set values — enter 0 if they do not apply.
- If you have a firm letterhead in PDF format, upload it on this page. Invoices will be automatically overlaid onto the letterhead.
- Go to the Lawyers page and add team members with their billing rates.
- Go to the Clients & Projects page and add your clients. On each matter page, you can enter the Engagement Letter Date — this will be automatically included in the invoice Re: line. The Billing Arrangement section is for reference only and does not affect invoice calculations.
- Go to the Users page to create login accounts for team members, link them to their lawyer profiles, and assign the matters they can access.

### 6.2 Generating invoices

1. Go to the Settings & Export page, select the matter, and enter the billing end date.
2. Review the time entry preview. If correct, click "Proceed to Adjustment".
3. On the adjustment page, review the unbilled expense summary. Enter the disbursements total (in the billing currency) in the Disbursements field. You may also adjust the Fees amount if needed. General Expenses and Local Tax are calculated automatically.
4. Once all amounts are confirmed, click "Download Invoice (PDF)" to generate and download the invoice. The relevant time entries and expenses will be permanently locked.
5. To download a Word version for manual formatting, click "Download Invoice (Word, no letterhead)". This does **not** lock any records.

*Note: If an error is found in a generated invoice, go to Invoice History to void it. The relevant records will be unlocked and the invoice can be regenerated.*

### 6.3 Accounts receivable

- Go to Invoice History to view payment status (Unpaid / Partial / Paid) for all invoices.
- Click a payment status badge to update the payment status, amount received, payment date, and notes.
- Invoices unpaid for more than 30 days from the invoice date are flagged in red. Use the Overdue filter to find them quickly.
- Voided invoices do not show a payment status.

### 6.4 Data backup

- Go to Settings, find the Data Backup section, and click "Download Backup".
- You will be prompted to choose a save location. The backup is packaged and downloaded as a zip file (filename: LexSheet-Backup-YYYY-MM-DD.zip).
- Back up regularly and store the zip file in a safe location (e.g. an external drive or cloud storage).

*Note: To restore data, close the software (close the start.bat window), extract the backup zip, copy all extracted files to the installation directory overwriting any existing files, then restart the software (run start.bat).*

*Data portability: If you decide to stop using LexSheet, time records and expense records can be exported as Excel files; invoices are already saved as PDF/Word files; the database backup serves as a complete long-term archive. Your data is not locked in.*

### 6.5 Audit log

- Go to the Audit Log page (administrator only) to view a complete record of all key operations.
- Filter by operation type and date range as needed.
- Click "Export Current View" to download the audit log as an Excel file. If no filters are active, all records are exported. If filters are applied, only the currently displayed records are exported.
- The audit log cannot be edited or deleted through the application interface — all entries are durably preserved.

---

## VII. Team Member Guide

- Open the software in a browser and log in with the account provided by your administrator.
- On first login, go to the password change option in the navigation bar to set your own password.
- Under the Time Entries tab, log your daily hours: select a matter, describe the work, and enter the number of hours.
- Under the Expenses tab, log disbursements: select a matter, choose a category, and enter the amount and currency.
- View, edit, or delete your unlocked entries in the My Entries and My Expenses tables.
- Download your timesheet (Excel) or expense report (Excel) at any time.

*Note: Time entries are automatically locked 10 days after the date of work and cannot be edited or deleted after that. If a locked entry needs to be corrected, contact your administrator to unlock it.*

---

## VIII. FAQ

**Q: I forgot my password. What should I do?**

Normal users should contact their administrator. Administrators can reset passwords from the Users page.

If an administrator forgets their own password, they can use the **recovery code** generated each time a password is changed. On the login page, click "Forgot password?", enter your username and recovery code, and you will be able to set a new password. The recovery code is displayed once after each password change — please keep it in a safe place.

**If the recovery code is also lost:** please note that because LexSheet is built on a zero-data-collection architecture, the developer has no way to access or verify any user's identity, and therefore **cannot verify an administrator's identity or provide a password reset in the event the recovery code is also lost**. Safeguarding the recovery code is the administrator's responsibility.

**Q: I can't open the software in my browser. What should I check?**

- Confirm that the start.bat window is still running on the server
- Confirm the address is correct (use localhost for local access; use the networking tool's IP for remote access)
- If using Tailscale, confirm that your device shows a Connected status

**Q: I see "HTTP ERROR 502" when accessing remotely. What's wrong?**

If your computer is running proxy software such as Clash with TUN mode enabled, this can cause 502 errors. Try disabling TUN mode temporarily, or add the networking tool's address range (100.64.0.0/10 for Tailscale) to your proxy software's bypass list.

**Q: How do I back up my data?**

Use the Download Backup button in the Data Backup section of the Settings page. You will be prompted to choose a save location, and the system will package the database files automatically. Back up regularly.

**Q: The server machine has failed. How do I recover?**

Run the installer on a new machine, then extract your backup zip and copy all files to the new installation directory, overwriting any existing files. Run start.bat to restore all historical data.

**Q: There are warning messages in the command prompt window. Is something wrong?**

No. As long as "Ready" is shown, the software is running normally.

---

*For issues not covered by this guide, contact the developer: lexsheet@outlook.com*
