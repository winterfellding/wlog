### 关闭输入输出流

今天在写一个对图片处理的方法的时候，自己给自己挖了个坑，具体代码如下：

	FileOutputStream out = null;
    try {
        BufferedImage image = new BufferedImage(middleW, middleH, BufferedImage.TYPE_INT_RGB);
        image.getGraphics().drawImage(srcImage, 0, 0, middleW, middleH, null);  
        out = new FileOutputStream(destFileMiddle);  
        ImageIO.write(image, "jpg", out);
        
        BufferedImage smallImage = new BufferedImage(w, h, BufferedImage.TYPE_INT_RGB); 
        smallImage.getGraphics().drawImage(srcImage, 0, 0, w, h, x1, y1, x2, y2, null);
        out = new FileOutputStream(destFile);
        ImageIO.write(_small_image, "jpg", out);
        
    } catch(Exception e) {
		logger.error(e);
    }
    finally {
    	if (out != null) {
	        out.flush();  
	        out.close();  
    	}
    }
这里的FileOutputStream在用完之后又重新赋值了小图的FileOutputStream，之后在跑这个程序的时候，会导
致，之前的FileOutputStream并没有flush和close，那个图相当于在持续使用中，没法被打开，之后这个流也
不会被gc抓住了释放掉，所以正确方法应该再new一个流，然后在使用完毕后flush close释放掉资源。

	FileOutputStream out = null;

	FileOutputStream outMiddle = null;

    try {
        BufferedImage image = new BufferedImage(middleW, middleH, BufferedImage.TYPE_INT_RGB);
        image.getGraphics().drawImage(srcImage, 0, 0, middleW, middleH, null);  
        outMiddle = new FileOutputStream(destFileMiddle);  
        ImageIO.write(image, "jpg", outMiddle);
        
        BufferedImage smallImage = new BufferedImage(w, h, BufferedImage.TYPE_INT_RGB); 
        smallImage.getGraphics().drawImage(srcImage, 0, 0, w, h, x1, y1, x2, y2, null);
        out = new FileOutputStream(destFile);
        ImageIO.write(_small_image, "jpg", out);
        
    } catch(Exception e) {
		logger.error(e);
    }
    finally {
    	if (out != null) {
			outMiddle.flush();
			outMiddle.close();
	        out.flush();  
	        out.close();  
    	}
    }