desc "Rename everything."
task :setup, :name do |t, args|

    if ENV["PHASER"]
        phaser
    end

    if ENV["PIXI"]
        pixi
    end

    app_name = args[:name]
    `grep -lir APP_NAME_LOWER . | xargs -I{} sed -i -e $'s/APP_NAME_LOWER/#{app_name.downcase}/g' {}`
    `grep -lir APP_NAME . | xargs -I{} sed -i -e $'s/APP_NAME/#{app_name}/g' {}`
    `rm -fr *-e`
    `rm -fr src/*-e`
    #rename the entry point coffeescript file to the app title
    `mv src/app/entry_point.coffee src/app/#{app_name.downcase}.coffee`
    #remove the skeleton remote so this can be hacked on like a champ
    `git remote rm origin`
end

desc "Startup python server"
task :run do
    puts "Serving on port 8000!"
    `python -m SimpleHTTPServer` 
end


def phaser
    `wget 'https://raw.github.com/photonstorm/phaser/blob/master/build/phaser.js' -O lib/`
    add_script_to_index "phaser.js"
end

def pixi
    `wget 'https://raw.github.com/GoodBoyDigital/pixi.js/blob/master/bin/pixi.dev.js' -O lib/`
    add_script_to_index "pixi.dev.js"
end

def add_script_to_index script_name
    f = File.open("index.html")
    lines = f.readlines
    pl_index = 0

    lines.each_with_index{ |line, index| pl_index = index if line.include? "this is where the magic happens" }

    if pl_index == 0
       puts "magic not found, quitting." 
       exit 1
    end

    script_tag = "<script type=\"text/javascript\" src=\"#{ "lib/" + script_name }\"></script>\n"

    lines.insert pl_index, script_tag

    f = File.new "index.html", "w"
    lines.each { |l| f << l }
end
