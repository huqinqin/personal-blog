  ()如何使用grunt的uglify
  1. 安装nodejs
  2. 安装grunt-CLI
     npm install -g grunt -cli
  3. 创建一个简单的网站
    在D:/下建立一个文件夹，包含三个空文件夹，两个空文档，文件夹的名字是：build src test，两个空文档是：gruntfile.js和
    package.json.配置 package.json
    package.json的配置如下：
    {
  "name": "grunt_test",
  "version": "1.0.0",
  "devDependencies": {
   
  }
 }
还有，最后一个“devDependencies”是什么意思？字面意思解释是“开发依赖项”，即我们现在这个系统，将会依赖于哪些工具来开发。现在代码一行都没有写，依赖于谁？谁也不依赖！所以，就先写一个空对象。但是下文会慢慢把它填充起来。
 4 安装grunt
   npm install grunt --save-dev
 “—save-dev”的意思是，在当前目录安装grunt的同时，顺便把grunt保存为这个目录的开发依赖项。看到“开发依赖项”这一次，是不是觉得有些眼熟？上文在配置package.json时，其中的“devDependencies”中就会存储开发依赖项。
 具体保存为开发依赖项是一个什么效果？动手安装一下就是了。首先，在运行安装grunt的命令之前，package.json中的“devDependencies”对应的是空对象现在我们来运行这行命令。你会看到几条warning提示，不用管它。然后接下来就是加载状态，一个旋转的小横线。稍等待一会儿，会提示你安装成功。
 5. 配置Gruntfile.js
　　顾名思义，Gruntfile.js 这个文件，肯定是为了grunt做某种配置的。按照grunt的规定，我们首先把Gruntfile.js配置成如下格式。
   详情请参考网址：http://blog.csdn.net/wangfupeng1988/article/details/46418203/   (这个网址的内容写的很好也很详细)
   
   
  gruntfile.js 的配置
module.exports=function(grunt){
	//任务配置，所有插件的配置信息
	/*grunt.initConfig({
		//获取package.json的信息
		pkg:grunt.file.readJSON('package.json'),
		uglify:{
			options:{
				stripBanners:true;
				banner: '/!*!<%=pkg.name%>-<%=pkg.version%>.js <%=grunt.template.today("yyyy-mm-dd")%>*!/ \n'
			},
			build:{
				src:'src/test.js',
				dest:'build/<%=pkg.name%>-<%=pkg.version%>.js.min.js',
			}
		}
	});*/


	/*grunt.initConfig({
		pkg: grunt.file.readJSON('package.json'),
		uglify: {
			options: {
				banner: '/!*! <%= pkg.name %> - v<%= pkg.version %> - ' +
				'<%= grunt.template.today("yyyy-mm-dd") %> *!/'
			},
			my_target: {
				files: {
					'dest/test.min.js': ['src/test.js']
				}
			}
		}
	});*/



	/*grunt.initConfig({
	 pkg: grunt.file.readJSON('package.json'),
		uglify: {
			options: {
				compress: {
					global_defs: {
						'DEBUG': false
					},
					dead_code: true
				}
			},
			my_target: {
				files: {
					'dest/test.min.js': ['src/test1.js']
				}
			}
		}
	});*/

	grunt.initConfig({
		pkg: grunt.file.readJSON('package.json'),


		uglify: {
			options: {
				mangle: false
			},
			my_target: {
				files: {
					'dest/output.min.js': ['js/angular-double.js']
				}
			}
		},

		jshint: {
			options: {
				/*"bitwise": true,
				"curly": false,
				"eqeqeq": false,
				"es3": true,
				"freeze": true,
				"funcscrop": true,
				"futurehostile": true,
				"latedef": true,
				"noarg": true,
				"nonbsp": true,
				"notypeof": true,
				"undef": true,
				"unused": true,
				"asi": true,
				"eqnull": true,
				"evil": true,
				"loopfunc": true,
				"plusplus": false,
				"validthis": true,
				"withstmt": true,
				"browser": true,
				"jquery": true,
				"strict":false,*/
				"globals": {
					"angular"   : false,
					"jasmine"   : false,
					"$"         : false,
					"_"         : false,
					"module"    : false,
					"require"   : false,
					"console":false
				}

			},
			//具体任务配置
			files: {
				src: ['js/angular-double.js']
			}
		},

		watch: {
			scripts: {
				files: ['src/angular-double.js'],
				tasks: ['jshint'],
				options: {
					spawn: false,
				},
			},
		},
	});






	//告诉grunt当我们在终端输入grunt时需要做些什么（注意先后顺序）
	grunt.loadNpmTasks('grunt-contrib-uglify');
/*
	grunt.loadNpmTasks('grunt-contrib-jshint');
*/
	/*grunt.registerTask('default',[]);*/
	// 加载指定插件任务
	grunt.loadNpmTasks('grunt-contrib-jshint');
	grunt.loadNpmTasks('grunt-contrib-watch');

	// 默认执行的任务
/*
	grunt.registerTask('default', ['uglify']);
*/
	grunt.registerTask('default', ['jshint','uglify','watch']);
/*	grunt.registerTask('default', ['watch']);*/

/*	grunt.registerTask('default',['uglify']);*/
};
