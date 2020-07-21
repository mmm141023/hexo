---
title: java实现文件压缩下载
date: 2020-07-20 18:45:47
tags:
---
需求同样来源于公司前段时间的项目

想要对文件进行压缩操作，这就需要用到ZipOutputStream来对文件压缩操作。首先需要指明的是：ZipOutputStream如果使用java自带的api操作需要1.7以上，否则会出现中文乱码，项目用的是1.8，使用它提供的ZipEntry和ZipOutputStream接口。

@GetMapping(value = "/xx/xx/download")
    public void downloadMulti(String operationId, HttpServletRequest request, HttpServletResponse response) {
        response.setContentType("application/octet-stream");
        response.setHeader("Content-Disposition", "attachment; filename="+new SimpleDateFormat("yyyyMMddHHmmss").format(new Date())+".zip");
        ZipOutputStream zipOutputStream = null;
        try {
            zipOutputStream = new ZipOutputStream(response.getOutputStream());
            List<a> aIds = aDao.findaByOperationId(Long.valueOf(operationId));
            ArrayList<String> fileNames = new ArrayList<>();
            int duplicate = 0;
            for (int i = 0; i < aIds.size(); i++) {
                String serviceName = aIds.get(i).getServiceName();
                String uuid = aIds.get(i).getUuid();
                //这边调的是共用的下载接口
                Response response1 = storageFeignClient.downloadFile(serviceName, uuid);
                Response.Body body = response1.body();
                InputStream inputStream = null;
                try {
                    inputStream = body.asInputStream();
                    //set name duplicate or not
                    String fileName = bDao.findByFlag(uuid).getFileName();
                    String[] split = fileName.split("\\.");
                    if (fileNames.contains(fileName)){
                        duplicate ++;
                    }
                    if (duplicate!=0){
                        zipOutputStream.putNextEntry(new ZipEntry(split[0]+"("+duplicate+")."+split[1]));
                        fileNames.add(split[0]+"("+duplicate+")."+split[1]);
                    }else {
                        zipOutputStream.putNextEntry(new ZipEntry(fileName));
                        fileNames.add(fileName);
                    }
                    //set ext
                    zipOutputStream.setComment(bDao.findByUuid(uuid).getExt());
                    int temp = 0;
                    while ((temp = inputStream.read()) != -1) {
                        zipOutputStream.write(temp);
                    }
                } catch (IOException e) {
                    e.printStackTrace();
                }
                inputStream.close();
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (null != zipOutputStream) {
                    zipOutputStream.flush();
                    zipOutputStream.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
 
        }
    }
 
 
（与项目有关的均已处理，还望理解）
