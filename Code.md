![图片](https://github.com/tanalala/CVE/assets/87268585/e4cf6d99-9806-4e4e-8022-ec7e4468bb3e)It is not directly required to retrieve and verify in the jar package within the project
It can be seen that not achieving one code at a time results in the verification code being continuously reused

Vulnerability Address：
net\mingsoft\ms-basic\2.1.8\ms-basic-2.1.8-sources.jar!\net\mingsoft\basic\action


Vulnerability code：
```
@PostMapping(value = "/checkLogin")
    @ResponseBody
    public ResultData checkLogin(@ModelAttribute @ApiIgnore ManagerEntity manager, HttpServletRequest request, HttpServletResponse response) {
        LOG.debug("basic checkLogin");

        //验证码
        if (!(checkRandCode())) {
            return ResultData.build().error(getResString("err.error", this.getResString("rand.code")));
        }
        if(loginStrategy.login(manager)){
            return ResultData.build().success();
        }else {
            return ResultData.build().error(getResString("err.error", this.getResString("manager.name.or.password")));
        }

    }
}

protected boolean checkRandCode( String param) {
		if(!checkCode){
			return true;
		}
		String sessionCode = this.getRandCode();
		String requestCode = BasicUtil.getString(param);
		LOG.debug("session_code:" + sessionCode + " requestCode:" + requestCode);
		if (sessionCode.equalsIgnoreCase(requestCode)) {
			return true;
		}
		return false;
	}
```
Vulnerability verification:
You can see that by modifying the password parameters, the value can be exploded and successfully verified. The code is reused
![图片](https://github.com/tanalala/CVE/assets/87268585/6a5b2322-4d1d-420f-b459-2a2a9cfc6fde)
![图片](https://github.com/tanalala/CVE/assets/87268585/05d6da31-1db3-4d0b-9e5f-7e370fc218c0)


