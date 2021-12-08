# pdfbox
pdfbox PDF转图片支持中文
在容器环境中无法安装中文字体，导致pdfbox 转图片时乱码


##自定义字体
修改org/apache/pdfbox/pdmodel/font目录下的字体文件，如org/apache/pdfbox/pdmodel/font/PDCIDFontType2Font.java
try
            {
                awtFont = Font.createFont( Font.TRUETYPE_FONT, ff2Stream.createInputStream() );
                // create a font with the embedded data
            }
            catch( FontFormatException f )
            {
                try {
                //找不到字体，就默认找org/apache/pdfbox/resources/ttc/simsun.ttc，修改其它font类似
                    awtFont = Font.createFont( Font.TRUETYPE_FONT,getClass().getClassLoader().getResource("org/apache/pdfbox/resources/ttc/simsun.ttc").openStream());
                } catch (FontFormatException e) {
                    e.printStackTrace();
                }

            }
