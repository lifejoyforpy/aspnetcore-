# aspnetcore-
#AuthenticationHttpContextExtensions
  AuthenticationHttpContextExtensions 是httpcontext对认证的扩展;
  SignInAsync 用户登录成功后颁发一个证书（加密的用户凭证），用来标识用户的身份。
  SignOutAsync 退出登录，如清除Coookie等。
  AuthenticateAsync 验证在 SignInAsync 中颁发的证书，并返回一个 AuthenticateResult 对象，表示用户的身份。
  ChallengeAsync 返回一个需要认证的标识来提示用户登录，通常会返回一个 401 状态码。
  ForbidAsync 禁上访问，表示用户权限不足，通常会返回一个 403 状态码。
  GetTokenAsync 用来获取 AuthenticationProperties 中保存的额外信息。
#AuthenticationCoreServiceCollectionExtensions
  具体的认证方法实现 实际是AuthenticationHttpContextExtensions 调用AuthenticationCoreServiceCollectionExtensions的
  同名方法
  提供Di;addAuthenticationCoreServices=>注入三大认证对象:
   IAuthenticationSchemeProvider,IAuthenticationHandlerProvider,IAuthenticationService
认证=> 认证方案  AuthenticationScheme => IAuthenticationSchemeProvider
AuthenticationScheme=> 包括name，displayname，handlertype(每个AuthenticationScheme 都有逻辑处理)
IAuthenticationSchemeProvider=> 提供实现 AuthenticationScheme 的注册查询;
(实现技巧是key value 存 AuthenticationScheme)同时获取配置参数(options)
AuteticationOptions=>AuthenticationScheme 的额外配置参数;
在 AuteticationOptions (key value 存储)
