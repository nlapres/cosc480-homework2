# in app/controllers/movies_controller.rb

class MoviesController < ApplicationController
  def index
		@all_ratings  = ['G', 'PG', 'PG-13', 'R']
		@sortby = params[:sort]
		keys = ['G', 'PG', 'PG-13', 'R']
		if params.has_key?(:ratings)
			keys = params[:ratings]
		end
		@selected_ratings = keys
		if params[:sort]=='title'
			@movies = Movie.where("rating IN (?)", keys).order("title ASC")
		elsif params[:sort]=='release_date'
			@movies = Movie.where("rating IN (?)", keys).order("release_date ASC")
		else
    	@movies = Movie.where("rating IN (?)", keys)
		end
  end

  def show
    id = params[:id]
    @movie = Movie.find(id)
    # will render app/views/movies/show.html.haml by default
  end

  def new
    # default: render 'new' template
  end

  def create
    @movie = Movie.create!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully created."
    redirect_to movies_path
  end

  def edit
    @movie = Movie.find params[:id]
  end

  def update
    @movie = Movie.find params[:id]
    @movie.update_attributes!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully updated."
    redirect_to movie_path(@movie)
  end

  def destroy
    @movie = Movie.find(params[:id])
    @movie.destroy
    flash[:notice] = "Movie '#{@movie.title}' deleted."
    redirect_to movies_path
  end
end
