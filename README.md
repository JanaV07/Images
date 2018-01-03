public static String generateInputODSC() {
		StringBuffer buf=new StringBuffer();
		System.out.println("PACKAGE NAME : :"+packageName);
		System.out.println("FUnction NAme : :"+functionName);
		String importStatemnt="package com.pershing.pdoservices."+packageName+".inparm;\nimport com.pershing.odsc.*;\nprivate final static OdscMetaData[] parameterInfo = new OdscMetaData[] {\n";
		buf.append(importStatemnt);
		int j=0;
		for(int i=0;i<observableInputItemList.size();i++) {
			ItemBase item=observableInputItemList.get(i);
			String type;
			if(item.getType().equals("String"))
				type="s";
			else if(item.getType().equals("Integer"))
					type="i";
			else if(fieldTypeList.contains(item.getType()))
				type="x";
			else type="undefined";
			buf.append("new OdscMetaData("+item.getName()+","+j+","+(j+Integer.parseInt(item.getSize()))+","+type+"),\n");
			j=j+Integer.parseInt((item.getSize()));
		}
