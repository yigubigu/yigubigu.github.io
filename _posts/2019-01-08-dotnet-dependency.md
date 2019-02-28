---
date: 2019-01-07 09:50:47+00:00
layout: post
title: 'dotnet dependency graph'
categories: 技术 
tags:  dotnet 
---


dotnet msbuild /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg
dotnet msbuild MySolution.sln /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg
