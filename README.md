����   3 �  .edu/isi/bmkeg/utils/svn/TestSVNEvaluateService  junit/framework/TestCase svnUtils "Ledu/isi/bmkeg/utils/svn/SvnUtils; temp Ljava/io/File; topDir svnDir LOGIN Ljava/lang/String; PASSWORD <clinit> ()V Code   	    	     LineNumberTable LocalVariableTable <init>
    	     this 0Ledu/isi/bmkeg/utils/svn/TestSVNEvaluateService; setUp 
Exceptions # java/lang/Exception RuntimeVisibleAnnotations Lorg/junit/Before; '  edu/isi/bmkeg/utils/svn/temp.txt
 ) + * java/lang/ClassLoader , - getSystemResource "(Ljava/lang/String;)Ljava/net/URL;
 / 1 0 java/net/URL 2 3 getPath ()Ljava/lang/String; 5 java/io/File 7 /
 9 ; : java/lang/String < = lastIndexOf (Ljava/lang/String;)I
 9 ? @ A 	substring (II)Ljava/lang/String;
 4 C  D (Ljava/lang/String;)V	  F 	  H java/lang/StringBuilder
 4 1
 9 K L M valueOf &(Ljava/lang/Object;)Ljava/lang/String;
 G C P /svnDir
 G R S T append -(Ljava/lang/String;)Ljava/lang/StringBuilder;
 G V W 3 toString	  Y 
 
 4 [ \ ] exists ()Z
 4 _ ` ] delete
 4 b c ] mkdir url Ljava/net/URL; path StackMapTable tearDown Lorg/junit/After; testRunEvaluation Lorg/junit/Test;
 9 m n o length ()I q  edu/isi/bmkeg/utils/svn/SvnUtils s Hhttps://hugin.isi.edu:1739/svn/repository/code/utils/trunk/src/main/java
 p u  v G(Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;Ljava/io/File;)V
 G 
 G y S z -(Ljava/lang/Object;)Ljava/lang/StringBuilder; | /MANIFEST.MF ~ META-INF/MANIFEST.MF
 p � � � getEntry #(Ljava/lang/String;Ljava/io/File;)V
 4 � n � ()J � "Manifest file expected to be 39B:        '
  � � � assertEquals (Ljava/lang/String;JJ)V thisCode fileSize J testCheckout
 p � � � checkout v manifest testCheckForChanges � /META-INF/MANIFEST.MF � java/io/BufferedWriter � java/io/FileWriter
 � �  � (Ljava/io/File;)V
 � �  � (Ljava/io/Writer;)V � ARGH
 � � � java/io/Writer � D write
 � � �  close
 p � � ] checkForChange
  � � � 
assertTrue (Z)V output Ljava/io/Writer; check Z � java/lang/Throwable 
SourceFile TestSVNEvaluateService.java !                 	     
    
     
             /      � � �       
                    <     
*� *� �              	         
          !     " $     %      �     `&� (L+� .M*� 4Y,,6� 8� >� B� E*� 4Y� GY*� E� I� J� NO� Q� U� B� X*� X� Z� *� X� ^W*� X� aW�       "          ! ! E # O $ W & _ (         `      Z d e   U f   g    � W / 9  h   !     " $     i      +      �           .              j   !     " $     k      �     X� � l� �*� pYr� � *� X� t� � 4Y� GY� w*� X� x{� Q� U� BL*� }+� +� �A� � � ��       B    3 	 5 
 8  9  :  ;  <  8 ! ? ? @ C A E B F @ I D N F W H         X     ?  �   N 
 � �  g    
  �   !     " $     k      �     D� � l� �*� � �@� 4Y� GY*� X� I� J� N{� Q� U� BN-� �7� �� ��           M 	 O 
 R  T 3 U 9 V C X    *    D      2 � �  3  �   9  � �  g    
  �   !     " $     k          l� � l� �*� � �@� 4Y� GY*� X� I� J� N�� Q� U� BN� �Y� �Y-� �� �:�� �� :� ��� �*� � �6� ��  D N N       6    ] 	 _ 
 b  d 3 e D g K h P i U j X i ] l f m k o    4    l      Z � �  3 9    D ( � �  f  � �  g    
� C   4 �  �	  �    �